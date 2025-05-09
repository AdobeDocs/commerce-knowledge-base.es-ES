---
title: "ACSD-53347: El rendimiento de la indexación de precios se degrada gradualmente con el paso del tiempo"
description: Aplique el parche ACSD-53347 para corregir el problema de Adobe Commerce en el que el rendimiento se degrada gradualmente al reindexar los precios de un catálogo de productos grande.
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347: El rendimiento de la indexación de precios se degrada gradualmente con el tiempo

El parche ACSD-53347 corrige el problema en el que el rendimiento se degrada gradualmente al reindexar los precios de un catálogo de productos grande. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38. El ID del parche es ACSD-53347. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al reindexar los precios de un catálogo de productos grande, el rendimiento de las consultas ejecutadas durante el proceso de indexación se degrada gradualmente.

<u>Pasos a seguir</u>:

1. Cree un catálogo grande y simple y asigne opciones personalizadas a estos productos (las opciones personalizadas utilizan una tabla temporal durante la indexación).
1. Cree al menos 200 grupos de clientes para aumentar la visibilidad del problema.
1. Cree diez o más sitios web y asigne todos los productos a cada uno.
1. Tenga en cuenta que los productos importados son casi idénticos, y solo difieren por SKU y nombre.
1. Habilitar **[!UICONTROL DB Logging]**.
1. Ejecute el comando `bin/magento index:reindex catalog_product_price`.
1. Compruebe si hay *DELETE DE`catalog_product_index_price_opt_agr_temp`* en `db.log`.

<u>Resultados esperados</u>:

La ejecución de *consultas de base de datos* se ejecuta correctamente.

<u>Resultados reales</u>:

El rendimiento de las *consultas de BD* en tablas temporales se ralentiza con el tiempo, por lo que la tabla de indexación de precios tarda mucho tiempo en completarse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
