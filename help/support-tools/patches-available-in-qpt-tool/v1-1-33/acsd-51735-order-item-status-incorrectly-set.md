---
title: "ACSD-51735: el estado del elemento de pedido se estableció incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0"
description: Aplique el parche ACSD-51735 para corregir el problema de Adobe Commerce en el que el estado del elemento de pedido se establece incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0.
feature: Orders, Products
role: Admin
exl-id: c6376698-71dc-46b8-a5b2-86dc26a574ab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735: el estado del elemento de pedido se estableció incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0

El parche ACSD-51735 corrige el problema en el que el estado del elemento de pedido se establece incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. El ID del parche es ACSD-50895. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado del artículo de pedido se establece incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0.

<u>Requisitos previos</u>:

* Los módulos de Adobe Commerce Inventory management (MSI) están instalados.
* Los pedidos no satisfechos están habilitados en **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Pasos a seguir</u>:

1. Cree un nuevo inventario de stock.
1. Cree una nueva fuente.
1. Asigne el sitio web predeterminado al nuevo inventario y asigne el nuevo origen.
1. Cree un nuevo producto.

   * Establezca la cantidad de origen predeterminada en 10 y la nueva cantidad de origen en 0.

1. Añadir el producto al carro de compras en la tienda.
1. Observe la advertencia de pedido pendiente al cerrar la compra, lo que indica que el producto proviene de una nueva fuente.
1. Realice el pedido.
1. Abra el pedido en Administración y compruebe el estado del pedido pendiente.

<u>Resultados esperados</u>:

El orden muestra que la cantidad 1 está en espera.

<u>Resultados reales</u>:

El orden muestra que la cantidad 1 está ordenada, no pendiente.

>[!MORELIKETHIS]
>
>[El estado del elemento de pedido se ha establecido incorrectamente en *[!UICONTROL Backordered]*](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
