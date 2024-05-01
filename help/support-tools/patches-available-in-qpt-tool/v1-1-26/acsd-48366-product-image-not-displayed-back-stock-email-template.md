---
title: '"ACSD-48366: la imagen del producto no se muestra en [!UICONTROL Back to Stock] plantilla de correo electrónico'''
description: Aplique el parche ACSD-48366 para corregir el problema de Adobe Commerce en el que la imagen en miniatura del producto no se muestra en el correo electrónico de alerta de existencias del producto.
exl-id: 57b549b0-6e97-4d5f-927e-9585f3257872
feature: Admin Workspace, Communications, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48366: la imagen del producto no se muestra en [!UICONTROL Back to Stock] plantilla de correo electrónico

El parche ACSD-48366 corrige el problema en el que la imagen en miniatura del producto no se muestra en el correo electrónico de alerta de existencias del producto. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 está instalado. El ID del parche es ACSD-48366. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La imagen del producto no se muestra en la [!UICONTROL Back to Stock] plantilla de correo electrónico.

<u>Pasos a seguir</u>:

1. Activar *[!UICONTROL Product Alert]* para *[!UICONTROL Back in Stock]* al ir a **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Activar *[!UICONTROL Display Out of Stock Products]* al ir a **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Cree un producto simple con cantidad = 0.
1. Cree un cliente desde la tienda y suscríbase al producto anterior para recibir alertas de productos cuando esté disponible.
1. Haga que el producto esté en stock.
1. Ejecute la alerta de producto cron.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Inicie la alerta de producto para el cliente.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Compruebe el correo electrónico. El correo electrónico de alerta de stock debería estar disponible en el receptor de correo.

<u>Resultados esperados</u>:

La imagen del producto se muestra en el correo electrónico de alerta de stock.

<u>Resultados reales</u>:

La imagen del producto no está disponible en el correo electrónico de alerta de stock.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
