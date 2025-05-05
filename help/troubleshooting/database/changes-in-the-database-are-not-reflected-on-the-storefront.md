---
title: Los cambios en la base de datos no se reflejan en la tienda
description: Este artículo proporciona soluciones para evitar retrasos o interrupciones en la aplicación de las actualizaciones de entidades. Esto incluye cómo evitar que las tablas de registro de cambios se sobredimensionen y cómo configurar  [!DNL MySQL] déclencheur de tabla.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Los cambios en la base de datos no se reflejan en la tienda

Este artículo proporciona soluciones para evitar retrasos o interrupciones en la aplicación de las actualizaciones de entidades. Esto incluye cómo evitar que las tablas del registro de cambios se sobredimensionen y cómo configurar [!DNL MySQL] déclencheur de tabla.

Productos y versiones afectados:

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* Adobe Commerce local 2.2.x, 2.3.x

## Problema

Los cambios que realice en la base de datos no se reflejan en la tienda o hay un retraso significativo en la aplicación de las actualizaciones de entidad. Las entidades que pueden verse afectadas incluyen productos, categorías, precios, inventario, reglas de catálogo, reglas de ventas y reglas de destino.

## Causa

Si los indexadores están [configurados para actualizarse según la programación](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers), el problema podría deberse a una o más tablas con registros de cambios demasiado grandes o a que no se han configurado déclencheur MySQL.

### Tablas de registro de cambios sobredimensionadas

Las tablas de registro de cambios crecen de ese modo si el trabajo cron de `indexer_update_all_views` no se completa correctamente varias veces.

Las tablas de registro de cambios son las tablas de base de datos en las que se realiza un seguimiento de los cambios en las entidades. Un registro se almacena en una tabla de registro de cambios mientras no se aplique el cambio, que realiza el trabajo cron de `indexer_update_all_views`. Hay varias tablas de registro de cambios en una base de datos de Adobe Commerce, y se les asigna un nombre según el siguiente patrón: INDEXER\_TABLE\_NAME + &#39;\_cl&#39;, por ejemplo `catalog_category_product_cl`, `catalog_product_category_cl`. Puede encontrar más detalles sobre cómo se realiza el seguimiento de los cambios en la base de datos en el artículo [Resumen de la indexación > Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) de nuestra documentación para desarrolladores.

### [!DNL MySQL] déclencheur de base de datos no configurados

Sospecharía que no se han configurado déclencheur de base de datos, si después de agregar o cambiar una entidad (producto, categoría, regla de destino, etc.) - no se agregan registros a la tabla de registro de cambios correspondiente.

## Solución

>[!WARNING]
>
>Se recomienda encarecidamente crear una copia de seguridad de la base de datos antes de realizar cualquier manipulación y evitarlas durante períodos de carga alta del sitio.

### Evite el sobretamaño de las tablas del registro de cambios

Asegúrese de que el trabajo cron de `indexer_update_all_views` siempre se complete correctamente.

Puede utilizar la siguiente consulta SQL para obtener todas las instancias erróneas del trabajo cron `indexer_update_all_views`:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

O puede comprobar su estado en los registros buscando las `indexer_update_all_views` entradas:

* `<install_directory>/var/log/cron.log`: para las versiones 2.3.1+ y 2.2.8+
* `<install_directory>/var/log/system.log` - para versiones anteriores

### Volver a establecer [!DNL MySQL] déclencheur de tabla

Para configurar los déclencheur de tabla [!DNL MySQL] que faltan, debe volver a establecer el modo de indizador:

1. Cambie a &quot;Al guardar&quot;.
1. Cambie a &quot;Según lo programado&quot;.

Utilice el siguiente comando para realizar esta operación.

>[!WARNING]
>
>Antes de cambiar los modos del indizador, recomendamos poner su sitio web en modo [mantenimiento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=es#maintenance-mode) y [deshabilitar los trabajos cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=es#disable-cron-jobs) para evitar bloqueos de la base de datos.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>Los déclencheur de base de datos relacionados con los indexadores se agregan cuando el modo de indexador se establece en programación y se eliminan cuando el modo de indexador se establece en tiempo real. Si faltan los déclencheur en la base de datos mientras los indexadores están configurados en la programación, cambie los indexadores a tiempo real y vuelva a cambiarlos a la programación. Esto restablece los déclencheur.

## Lectura relacionada

* [[!DNL MySQL] las tablas son demasiado grandes](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-tables-are-too-large) en nuestra base de conocimiento de soporte
* [Indexación: [!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) en nuestra documentación para desarrolladores
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
