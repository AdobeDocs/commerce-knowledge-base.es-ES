---
title: '"ACSD-53750: Error de "Tubería rota o conexión cerrada" durante el reíndice catalog_product_price multiproceso"'
description: Aplique el parche ACSD-53750 para corregir el problema de Adobe Commerce en el que se produce un error de *Conexión rota o Conexión cerrada* durante el reíndice catalog_product_price multiproceso.
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750: *Tubo roto o conexión cerrada* error durante procesos múltiples `catalog_product_price` reindexar

El parche ACSD-53750 corrige el problema en el que un *Tubo roto o conexión cerrada* se produce un error durante la ejecución de varios procesos `catalog_product_price` reindexe. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.37 está instalado. El ID del parche es ACSD-53750. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

*Tubo roto o conexión cerrada* se produce un error durante la ejecución de varios procesos `catalog_product_price` reindexe.

<u>Pasos a seguir</u>:

1. Configure RabbitMq.
1. Generar datos de ejemplo con el adjunto `small.xml` archivo.
1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** y establecer **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Establezca el modo de dimensión para los índices que admitan esto. Por ejemplo,. `catalog_product_price_website_and_customer_group` o `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Ejecutar el restablecimiento de los indexadores para `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Ejecute el indexador para el indexador de restablecimiento utilizando varios subprocesos.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Resultados esperados</u>:

No se producen errores.

<u>Resultados reales</u>:

El siguiente error está causado por una conexión AMQP: *Tubo roto o conexión cerrada*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
