---
title: '"ACSD-51408: El estado del elemento de pedido se ha establecido incorrectamente en [!UICONTROL backordered]'''
description: Aplique el parche ACSD-51408 para corregir el problema de Adobe Commerce en el que el estado del elemento de pedido está configurado incorrectamente como [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408: el estado del artículo de pedido se ha establecido incorrectamente en *[!UICONTROL backordered]*

El parche ACSD-51408 corrige el problema en el que el estado del elemento de pedido se establece incorrectamente como [!UICONTROL backordered]. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. El ID del parche es ACSD-51408. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado del artículo de pedido se ha definido incorrectamente como *[!UICONTROL backordered]*.

<u>Requisitos previos</u>:

Los módulos Adobe Commerce B2B y Inventory management (MSI) están instalados.

<u>Pasos a seguir</u>:

1. Crear un nuevo sitio web, tienda y vista de tienda.
1. Cree una nueva fuente.
1. Cree un nuevo inventario vinculado al nuevo sitio web creado en el paso 1 y asigne el origen creado en el paso 2.
1. Cree una empresa y asígnela al nuevo sitio web creado en el paso 1.
1. Cree un nuevo cliente y asígnelo a la compañía creada en el paso 4.
1. Cree un producto, asígnelo al nuevo sitio web y configure las variables **[!UICONTROL default stock]** = *0*, y el **[!UICONTROL new stock]** a mayor que *0*.
1. Activar **[!UICONTROL backorders]**.
1. Activar **[!UICONTROL Check/Money Order]** método de pago para el nuevo ámbito del sitio web.
1. Habilite la **[!UICONTROL Flat Rate shipping method]** para el nuevo ámbito del sitio web.
1. Creación de un nuevo pedido desde **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. Seleccione el nuevo cliente creado en el paso 5.
1. Seleccione el nuevo almacén creado en el paso 1.
1. Elija el producto creado en el paso 6.
1. Rellene la información del pedido, incluidos los métodos de pago y envío.
1. Envíe el pedido.
1. Compruebe la *Estado del elemento*.

<u>Resultados esperados</u>

El artículo está disponible para su envío desde el inventario. El estado del elemento es *[!UICONTROL ordered]*.

<u>Resultados reales</u>

El estado del elemento es *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[El estado del artículo de pedido se ha definido incorrectamente como *[!UICONTROL Ordered]* cuando el stock de productos es 0.](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
