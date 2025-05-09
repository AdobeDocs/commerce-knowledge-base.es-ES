---
title: Catálogo de Live Search no sincronizado
description: Este artículo proporciona soluciones para el problema de Adobe Commerce en el que los datos del catálogo no se sincronizan correctamente al utilizar la extensión de Live Search.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: 5911b436fdcc08e695fb14d35784287945593815
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Catálogo de Live Search no sincronizado

Este artículo proporciona soluciones para el problema de Adobe Commerce en el que los datos del catálogo no se sincronizan correctamente al utilizar la extensión de Live Search.

## Productos y versiones afectados

* Adobe Commerce 2.4.x con la extensión Live Search instalada

## Problema

Los datos del catálogo no están sincronizados correctamente o se ha añadido un nuevo producto, pero no aparece en los resultados de búsqueda. También puede recibir el siguiente error en `var/log/exception.log`:

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>Los nombres de tabla `catalog_data_exporter_products` y `catalog_data_exporter_product_attributes` ahora se llaman `cde_products_feed` y `cde_product_attributes_feed` a partir de [!DNL Live Search] versión 4.2.1. Para los comerciantes de versiones anteriores a la 4.2.1, busque los datos en los nombres de tabla antiguos, `catalog_data_exporter_products` y `catalog_data_exporter_product_attributes`.

<u>Pasos a seguir</u>

1. Configure y conecte Live Search para su instancia de Adobe Commerce como se describe en [Instalar Live Search > Configurar claves API](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=es#configure-api-keys) en nuestra documentación de usuario.
1. Después de 30 minutos, verifica los datos del catálogo exportados como se describe en [Instalar Live Search > Verificar exportación](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=es#verify-export) en nuestra documentación de usuario.
1. Después de 30 minutos, prueba la conexión tal como se describe en [Instalar Live Search > Probar la conexión](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=es#test-connection) en nuestra documentación de usuario.

O

1. Añadir un nuevo producto al catálogo.
1. Intente ejecutar una consulta de búsqueda utilizando el nombre del producto u otros atributos en los que se pueda buscar después de 15 a 20 minutos desde el momento en que indexador de Magento + cron se han ejecutado para sincronizar los datos con el servicio back-end.

<u>Resultado esperado</u>

* Se pueden verificar los datos del catálogo exportados
* Conexión correcta
* El nuevo producto aparece en los resultados de búsqueda.

<u>Resultado real</u>

El catálogo exportado no se puede verificar o no se ha establecido la conexión porque la clave de API ha cambiado.

## Solución

Hay varias cosas que puede hacer para intentar solucionar los problemas de sincronización del catálogo.

### Esperar a que se apliquen los cambios

Una vez configurada y conectada, puede tardar más de 30 minutos en crearse el índice en ES (Elasticsearch) y en devolver los resultados de búsqueda. Se espera que las posteriores actualizaciones de producto únicas se indexen en unos minutos.

### Sincronizar datos de producto para un SKU específico

Si los datos del producto no están sincronizados correctamente para un SKU específico, haga lo siguiente:

1. Utilice la siguiente consulta [!DNL SQL] y compruebe que dispone de los datos esperados en la columna `feed_data`. Además, anote la marca de tiempo `modified_at`.

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '<your_sku>' AND json_extract(feed_data, '$.storeViewCode') = '<your_ store_view_code>';
   ```

   Por ejemplo:

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '24-MB04' AND json_extract(feed_data, '$.storeViewCode') = 'default';
   ```

1. Si no ve los datos correctos, intente reindexar con el siguiente comando y vuelva a ejecutar la consulta [!DNL SQL] en el paso 1 para comprobar los datos:

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. Si sigue sin ver los datos correctos, [cree un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Comprobar la marca de tiempo de la última exportación del producto

1. Si ve los datos correctos en `cde_products_feed`, utilice la siguiente consulta [!DNL SQL] para comprobar la marca de tiempo de la última exportación. Debe ser posterior a la marca de tiempo `modified_at`:

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Si la marca de tiempo es anterior, puede esperar a la siguiente ejecución de cron o almacenarla en déclencheur mediante el siguiente comando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Espere `<>` tiempo (tiempo para actualizaciones incrementales). Si todavía no ves tus datos, [crea un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Sincronizar código de atributo específico

Si los datos de atributos del producto no están sincronizados correctamente para un código de atributo específico, haga lo siguiente:

1. Utilice la siguiente consulta [!DNL SQL] y compruebe que dispone de los datos esperados en la columna `feed_data`. Además, anote la marca de tiempo `modified_at`.

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Si no ve los datos correctos, utilice el comando siguiente para reindexar y, a continuación, vuelva a ejecutar la consulta [!DNL SQL] en el paso 1 para comprobar los datos.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. Si sigue sin ver los datos correctos, [cree un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Comprobar la marca de tiempo de la última exportación de atributos del producto

Si ve los datos correctos en `cde_product_attributes_feed`:

1. Utilice la siguiente consulta [!DNL SQL] para comprobar la marca de tiempo de la última exportación. Debe ser posterior a la marca de tiempo `modified_at`.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Si la marca de tiempo es anterior, puede esperar a la siguiente ejecución de cron o almacenarla en déclencheur mediante el siguiente comando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Espere entre 15 y 20 minutos (tiempo para actualizaciones incrementales). Si todavía no ves tus datos, [crea un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Sincronizar después del cambio de configuración de API

(Problema conocido) Si ha cambiado la configuración de la API, lo que provoca un cambio en el ID del espacio de datos y descubre que los cambios del catálogo ya no se sincronizan, ejecute los siguientes comandos para volver a sincronizar las fuentes:

```
bin/magento saas:resync --feed productattributes --cleanup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

[Envíe una solicitud de soporte técnico](https://experienceleague.adobe.com/home?lang=es&support-tab=home#support) para solicitar que se reindexe el índice de Live Search. En la descripción del problema, incluya el ID de espacio de datos/entorno que se encuentra en el panel de administración en **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]**.

>[!IMPORTANT]
>El uso de la opción `--cleanup-feed` en otros casos puede causar pérdida de datos y problemas de sincronización de datos.  Utilícelo solo cuando tenga un entorno nuevo vacío, después de que el equipo de Adobe haya completado una operación de limpieza del espacio de datos o cuando ejecute el comando `saas:resync` con la opción [—dry-run](https://experienceleague.adobe.com/es/docs/commerce/saas-data-export/data-export-cli-commands#--dry-run). El uso de la opción `--cleanup-feed` en otros casos puede causar pérdida de datos y problemas de sincronización de datos.

## Lectura relacionada

* [Incorporar Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html?lang=es) en nuestra documentación de usuario
* [Revisar registros y solucionar problemas de exportación y sincronización de datos de SaaS de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) en la Guía de exportación de datos de SaaS de Adobe Commerce
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
