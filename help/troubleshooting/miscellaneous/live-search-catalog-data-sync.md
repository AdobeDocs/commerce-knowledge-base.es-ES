---
title: Catálogo de Live Search no sincronizado
description: Este artículo proporciona soluciones para el problema de Adobe Commerce en el que los datos del catálogo no se sincronizan correctamente al utilizar la extensión de Live Search.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: ab39a21ca325cdad30debf89a1cff660bf5925e5
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%

---

# Catálogo de Live Search no sincronizado

Este artículo proporciona soluciones para el problema de Adobe Commerce en el que los datos del catálogo no se sincronizan correctamente al utilizar la extensión de Live Search.

## Productos y versiones afectados

* Adobe Commerce 2.4.x con la extensión Live Search instalada

## Problema

Los datos del catálogo no están sincronizados correctamente o se ha añadido un nuevo producto, pero no aparece en los resultados de búsqueda.

<u>Pasos a seguir</u>

1. Configure y conecte Live Search para su instancia de Adobe Commerce como se describe en [Instalar Live Search > Configurar claves API](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys) en nuestra documentación de usuario.
1. Después de 30 minutos, verifica los datos del catálogo exportados como se describe en [Instalar Live Search > Verificar exportación](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export) en nuestra documentación de usuario.
1. Después de 30 minutos, prueba la conexión tal como se describe en [Instalar Live Search > Probar la conexión](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection) en nuestra documentación de usuario.

O

1. Añadir un nuevo producto al catálogo.
1. Intente ejecutar una consulta de búsqueda utilizando el nombre del producto u otros atributos en los que se pueda buscar después de 15 a 20 minutos desde el indexador del Magento de tiempo + cron que se han ejecutado para sincronizar los datos con el servicio back-end.

<u>Resultado esperado</u>

* Se pueden verificar los datos del catálogo exportados
* Conexión correcta
* El nuevo producto aparece en los resultados de búsqueda.

<u>Resultado real</u>

El catálogo exportado no se puede verificar o no se ha establecido la conexión porque la clave de API ha cambiado.

## Solución

Hay varias cosas que puede hacer para intentar solucionar los problemas de sincronización del catálogo.

### Esperar a que se apliquen los cambios

Una vez configuradas y conectadas, el índice en ES (Elasticsearch) puede tardar más de 30 minutos en crearse y en devolver los resultados de búsqueda. Se espera que las posteriores actualizaciones de producto únicas se indexen en unos minutos.

### Sincronizar datos de producto para un SKU específico

Si los datos del producto no están sincronizados correctamente para un SKU específico, haga lo siguiente:

1. Utilice la siguiente consulta SQL y compruebe que dispone de los datos esperados en la columna `feed_data`. Además, anote la marca de tiempo `modified_at`.

   ```sql
   select * from catalog_data_exporter_products where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. Si no ve los datos correctos, intente reindexar con el siguiente comando y vuelva a ejecutar la consulta SQL en el paso 1 para comprobar los datos:

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_products
   ```

1. Si sigue sin ver los datos correctos, [cree un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Comprobar la marca de tiempo de la última exportación del producto

1. Si ve los datos correctos en `catalog_data_exporter_products`, utilice la siguiente consulta SQL para comprobar la marca de tiempo de la última exportación. Debe ser posterior a la marca de tiempo `modified_at`:

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

1. Utilice la siguiente consulta SQL y compruebe que dispone de los datos esperados en la columna `feed_data`. Además, anote la marca de tiempo `modified_at`.

   ```sql
   select * from catalog_data_exporter_product_attributes where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Si no ve los datos correctos, utilice el siguiente comando para reindexar y, a continuación, vuelva a ejecutar la consulta SQL en el paso 1 para comprobar los datos.

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_product_attributes
   ```

1. Si sigue sin ver los datos correctos, [cree un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Comprobar la marca de tiempo de la última exportación de atributos del producto

Si ve los datos correctos en `catalog_data_exporter_product_attributes`:

1. Utilice la siguiente consulta SQL para comprobar la marca de tiempo de la última exportación. Debe ser posterior a la marca de tiempo `modified_at`.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Si la marca de tiempo es anterior, puede esperar a la siguiente ejecución de cron o almacenarla en déclencheur mediante el siguiente comando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Espere entre 15 y 20 minutos (tiempo para actualizaciones incrementales). Si todavía no ves tus datos, [crea un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Sincronizar después del cambio de configuración de API

(Problema conocido) Si ha cambiado la configuración de la API, lo que provoca un cambio en el ID del espacio de datos y descubre que los cambios del catálogo ya no se sincronizan, ejecute los siguientes comandos:

```bash
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productattributes
```

## Lectura relacionada

* Consulte [Búsqueda en vivo integrada](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) en nuestra documentación de usuario.
* Consulte [Revisar registros y solucionar problemas de exportación y sincronización de datos SaaS de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) en la Guía de exportación de datos SaaS de Adobe Commerce.
