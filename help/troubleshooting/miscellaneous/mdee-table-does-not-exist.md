---
title: No existen datos corregidos que no se actualizaron en  [!DNL Commerce Data Exporter] fuentes y [!DNL cron] registros con errores de changelog
description: Este artículo proporciona una solución para solucionar los problemas de sincronización de datos causados por el uso de un id. de vista incorrecto en la suscripción  [!DNL Commerce Data Exporter mview] iOS.
feature: Data Import/Export, Saas, Logs
role: Developer
exl-id: 50f2223b-bfcf-4c3c-b0f1-dbcc4365edc2
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# No existen datos corregidos que no se hayan actualizado en [!DNL Commerce Data Exporter] fuentes y [!DNL cron] registros con errores de la tabla changelog

Este artículo proporciona una solución para solucionar los problemas de sincronización de datos causados por el uso del id. de vista incorrecto en la suscripción [!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview). La suscripción [!DNL Mview] se usa para realizar el seguimiento de los cambios de las tablas de la base de datos.

## Productos y versiones afectados

Instancias de Adobe Commerce donde se ha aplicado código personalizado a la funcionalidad de exportación de datos (`commerce-data-exporter` o `saas-exporter`). El error se produce si la versión de exportación de datos [[!DNL SaaS] instalada es 103.3.0](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) o posterior y el código hace referencia directamente al índice `catalog_data_exporter_products`.

## Problema

Es posible que los comerciantes descubran que faltan actualizaciones de datos en las tablas de fuentes del catálogo [!DNL Data Exporter] y vean los siguientes errores en los registros de trabajos de [!DNL cron]:

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## Causa

Debido a los cambios de nombre en las tablas de fuentes, índices y tablas de registro de cambios en la versión [!DNL Commerce Data Export] [versión 103.3.0](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/saas-data-export/release-notes#release-9), es posible que las suscripciones [!DNL Mview] en las extensiones personalizadas que usan extensiones [!DNL Commerce Data Export] no funcionen correctamente.

En este caso, el error *la tabla no existe* se produce porque el nombre de la tabla `catalog_data_exporter` se cambió a `cde_products_feed` y tiene código personalizado que hace referencia al nombre antiguo en la suscripción [!DNL Data Exporter Mview].

## Solución

En la extensión personalizada, edite el archivo de configuración [!DNL Mview] (```./etc/mview.xml```) para cambiar el nombre de tabla `catalog_data_exporter_products` a *`cde_products_feed`*.

En el ejemplo siguiente se muestra el código que especifica las tablas rastreadas por la suscripción [!DNL Mview]:

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## Lectura relacionada

* [[!DNL SaaS] Notas de la versión de Data Export Extension](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/saas-data-export/release-notes) en la Guía de exportación de datos de Adobe Commerce para [!DNL SaaS] servicios
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
