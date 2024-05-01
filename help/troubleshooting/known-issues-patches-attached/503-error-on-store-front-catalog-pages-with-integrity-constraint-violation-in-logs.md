---
title: Error 503 en las páginas del catálogo principal de la tienda con "Infracción de restricción de integridad" en los registros
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.0 relacionado con las páginas del catálogo de tienda que no son accesibles.
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Error 503 en las páginas del catálogo principal de la tienda con &quot;Infracción de restricción de integridad&quot; en los registros

>[!NOTE]
>
>Este artículo proporciona un parche como solución alternativa, pero el problema se solucionó de forma permanente en Adobe Commerce en la versión 2.3.3 de la infraestructura en la nube y se recomienda actualizar a la versión 2.3.3. Siga los pasos de [Actualizar la versión de Adobe Commerce](https://devdocs.magento.com/cloud/project/project-upgrade.html) en nuestra documentación para desarrolladores.

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.0 relacionado con las páginas del catálogo de tienda que no son accesibles, con un mensaje de error similar al siguiente en el registro: *Infracción de restricción de integridad: 1062 Entrada duplicada &#39;%entry%&#39; para la clave &#39;PRIMARY&#39;, consulta: INSERT INTO \`search\_tmp\_%number%*.

## Problema

Las páginas del catálogo principal de la tienda no son accesibles inesperadamente. El registro de errores tiene una descripción de error similar a la siguiente: *Infracción de restricción de integridad: 1062 Entrada duplicada &#39;%entry%&#39; para la clave &#39;PRIMARY&#39;, consulta: INSERT INTO \`search\_tmp\_%number%*.

El problema está relacionado con la búsqueda y causado por la existencia del índice obsoleto junto con el nuevo después de reindexar.

## Solución

Para solucionar el problema, debe eliminar los índices obsoletos de Elasticsearch y aplicar el parche para evitar que aparezcan.

Para enumerar todos los índices, utilice el siguiente comando:

<pre>curl -X GET %elasticsearch_domain%:%elasticsearch_port%/_cat/indices</pre>

Para eliminar los índices obsoletos, búsquelos en la base de datos y, a continuación, utilice el siguiente comando:

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

Ejemplo:

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## Parche

Los parches se adjuntan a este artículo. Para descargar un parche, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre de archivo necesario o haga clic en uno de los siguientes vínculos:

[Descargar MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[Descargar MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## Versiones de Adobe Commerce compatibles

Los parches se han creado para las siguientes ediciones y versiones:

* Adobe Commerce en la infraestructura en la nube 2.2.0 (`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)
* Adobe Commerce en la infraestructura en la nube 2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)

El `MDVA-9590_EE_2.2.0_COMPOSER_v2` Este parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en infraestructuras en la nube 2.0.X, 2.1.X, 2.2.X y 2.3.0 - 2.3.3
* Adobe Commerce local 2.0.X, 2.1.X, 2.2.X y 2.3.0 - 2.3.3

El `MDVA-13203_EE_2.2.4_V1_COMPOSER` Este parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en infraestructuras en la nube 2.0.X, 2.1.X, 2.2.X y 2.3.0 - 2.3.3
* Adobe Commerce local 2.0.X, 2.1.X, 2.2.X y 2.3.0 - 2.3.3

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Vínculos útiles

* [Ubicación de los archivos de registro para Adobe Commerce en la infraestructura de la nube](/help/how-to/general/log-locations-directories-for-starter-plan.md) en nuestra base de conocimiento de soporte.
* [Ubicación de los archivos de registro para Adobe Commerce en la infraestructura de la nube Arquitectura del plan Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) en nuestra base de conocimiento de soporte.
* [Ubicación de los archivos de registro para Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) en nuestra documentación para desarrolladores.

## Archivos adjuntos
