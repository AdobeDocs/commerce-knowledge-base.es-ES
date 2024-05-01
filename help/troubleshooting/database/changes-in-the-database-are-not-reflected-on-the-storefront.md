---
title: Los cambios en la base de datos no se reflejan en la tienda
description: Este artículo proporciona soluciones para evitar retrasos o interrupciones en la aplicación de las actualizaciones de entidades. Esto incluye cómo evitar que las tablas de registro de cambios se sobredimensionen y cómo configurar déclencheur de tabla MySQL.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Los cambios en la base de datos no se reflejan en la tienda

Este artículo proporciona soluciones para evitar retrasos o interrupciones en la aplicación de las actualizaciones de entidades. Esto incluye cómo evitar que las tablas de registro de cambios se sobredimensionen y cómo configurar déclencheur de tabla MySQL.

Productos y versiones afectados:

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* Adobe Commerce local 2.2.x, 2.3.x

## Problema

Los cambios que realice en la base de datos no se reflejan en la tienda o hay un retraso significativo en la aplicación de las actualizaciones de entidad. Las entidades que pueden verse afectadas incluyen productos, categorías, precios, inventario, reglas de catálogo, reglas de ventas y reglas de destino.

## Causa

Si los indexadores son [configurado para actualizar según lo programado](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers)Sin embargo, el problema puede deberse a una o más tablas con registros de cambios demasiado grandes o a que no se han configurado déclencheur MySQL.

### Tablas de registro de cambios sobredimensionadas

Las tablas del registro de cambios crecen de manera tan grande si la variable `indexer_update_all_views` el trabajo cron no se ha completado correctamente varias veces.

Las tablas de registro de cambios son las tablas de base de datos en las que se realiza un seguimiento de los cambios en las entidades. Un registro se almacena en una tabla de registro de cambios mientras no se aplique el cambio, que realiza el `indexer_update_all_views` trabajo cron. Existen varias tablas de registro de cambios en una base de datos de Adobe Commerce, con un nombre que se ajusta al siguiente patrón: INDEXER\_TABLE\_NAME + ‘\_cl’, por ejemplo `catalog_category_product_cl`, `catalog_product_category_cl`. Puede encontrar más detalles sobre cómo se realiza el seguimiento de los cambios en la base de datos en la [Resumen de indexación > Mview](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) artículo en nuestra documentación para desarrolladores.

### Déclencheur de base de datos MySQL no configurados

Sospecharía que no se han configurado déclencheur de base de datos, si después de agregar o cambiar una entidad (producto, categoría, regla de destino, etc.) - no se agregan registros a la tabla de registro de cambios correspondiente.

## Solución

>[!WARNING]
>
>Se recomienda encarecidamente crear una copia de seguridad de la base de datos antes de realizar cualquier manipulación y evitarlas durante períodos de carga alta del sitio.

### Evite el sobretamaño de las tablas del registro de cambios

Asegúrese de que la variable `indexer_update_all_views` el trabajo cron siempre se completa correctamente.

Puede utilizar la siguiente consulta SQL para obtener todas las instancias fallidas del `indexer_update_all_views` trabajo cron:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

O puede comprobar su estado en los registros buscando el `indexer_update_all_views` entradas:

* `<install_directory>/var/log/cron.log` - para las versiones 2.3.1+ y 2.2.8+
* `<install_directory>/var/log/system.log` - para versiones anteriores

### Restablecer déclencheur de tabla MySQL

Para configurar las déclencheur de tabla MySQL que faltan, debe volver a establecer el modo del indexador:

1. Cambie a &quot;Al guardar&quot;.
1. Cambie a &quot;Según lo programado&quot;.

Utilice el siguiente comando para realizar esta operación.

>[!WARNING]
>
>Antes de cambiar los modos del indexador, recomendamos colocar el sitio web en [mantenimiento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) modo y [deshabilitar trabajos de cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) para evitar bloqueos de la base de datos.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>Los déclencheur de base de datos relacionados con los indexadores se agregan cuando el modo de indexador se establece en programación y se eliminan cuando el modo de indexador se establece en tiempo real. Si faltan los déclencheur en la base de datos mientras los indexadores están configurados en la programación, cambie los indexadores a tiempo real y vuelva a cambiarlos a la programación. Esto restablece los déclencheur.

## Lectura relacionada

<ul><li title="Las tablas MySQL son demasiado grandes"><a href="/help/troubleshooting/database/mysql-tables-are-too-large.md">Las tablas MySQL son demasiado grandes</a> en nuestra base de conocimiento de soporte.</li>
<li title="Las tablas MySQL son demasiado grandes"><a href="https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview">Información general del indizador &gt; Mview</a> en nuestra documentación para desarrolladores.</li></ul>
