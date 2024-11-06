---
title: El Elasticsearch 5 está configurado, pero la página de búsqueda no se carga con el error "Los datos de campo están desactivados..."
description: 'En este tema se describe cómo solucionar el problema con Elasticsearch 5, donde la página de búsqueda no se carga y se genera la siguiente excepción:'
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# El Elasticsearch 5 está configurado, pero la página de búsqueda no se carga con el error &quot;Los datos de campo están desactivados...&quot;

En este tema se describe cómo solucionar el problema con el Elasticsearch 5, donde la página de búsqueda no se carga y se genera la siguiente excepción:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Versiones afectadas

* Adobe Commerce 2.2.x
* Elasticsearch v.5

>[!NOTE]
>
>Elasticsearch v.5 ya no se utiliza para Adobe Commerce 2.3.x

## Problema

Condiciones previas: el Elasticsearch 5 está configurado.

En la solicitud de búsqueda se genera la siguiente excepción en los registros:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Causa

De forma predeterminada, solo se pueden utilizar ciertos tipos de atributos de producto en la navegación por capas. Son Sí/No, Desplegable, Selección múltiple y Precio. Es por eso que en el administrador de Commerce no se puede establecer un atributo de ningún otro tipo como **Usar en navegación por capas** = *Filtrable* o **Usar en navegación por capas de resultados de búsqueda** = *Sí*. Pero existe una posibilidad técnica de evitar esta limitación cambiando directamente los valores `is_filterable` y `is_filterable_in_search` de la base de datos. Si esto sucede y cualquier otro tipo de atributo, como Fecha, Texto, etc., se configura para utilizarse en Navegación por capas, el Elasticsearch 5 genera una excepción.

Para asegurarse de que este sea el caso, debe averiguar si hay otros atributos que no sean Desplegable, Selección múltiple y Precio, que están configurados para utilizarse en la Navegación por capas. Ejecute la siguiente consulta para buscar estos atributos:

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

El resultado contendrá una lista de atributos utilizados para la navegación por capas, cuyo tipo no lo permite. Siga los pasos descritos en la siguiente sección para solucionarlo.

## Solución

Para solucionar el problema, debe establecer `is_filterable` (es decir, utilizado en la navegación por capas) y `filterable_in_search` (es decir, utilizado en la navegación por capas de los resultados de búsqueda) en &quot;0&quot; (no utilizado). Para ello, siga los siguientes pasos:

1. Cree una copia de seguridad de base de datos.
1. Use una herramienta de base de datos como [phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) o acceda a la base de datos manualmente desde la línea de comandos para ejecutar la siguiente consulta SQL:

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. Ejecute el reindexador completo Búsqueda en el catálogo utilizando el siguiente comando:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Limpiar la caché ejecutando

   ```bash
   bin/magento cache:clean
   ```

o en el Administrador de Commerce en **Sistema** > **Herramientas** > **Administración de caché**.

Ahora debería poder realizar búsquedas en el catálogo sin problemas.
