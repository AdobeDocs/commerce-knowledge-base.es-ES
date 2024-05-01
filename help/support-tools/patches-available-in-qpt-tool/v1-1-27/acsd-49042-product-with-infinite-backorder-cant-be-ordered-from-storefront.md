---
title: "ACSD-49042: El producto con un pedido pendiente infinito no se puede pedir desde la tienda"
description: Aplique el parche ACSD-49042 para corregir el problema de Adobe Commerce en el que un producto con un pedido pendiente infinito no se puede pedir desde la tienda.
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042: El producto con un pedido pendiente infinito no se puede pedir desde la tienda

El parche ACSD-49042 soluciona el problema de que un producto con un pedido pendiente infinito no se puede pedir desde la tienda. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. El ID del parche es ACSD-49042. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El error se produce cuando un producto con un pedido pendiente infinito no se puede pedir desde la tienda.

<u>Pasos a seguir</u>:

1. Establezca las siguientes opciones de configuración:
   * **[!UICONTROL Display Out of Stock Products]** establezca en *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** establezca en *[!UICONTROL Allow Qty Below 0]*.
1. Añadir un nuevo **[!DNL custom stock]** y **[!DNL custom source]**.
1. Asigne un producto a **[!DNL custom source]** y asegúrese de que haya un número de inventario establecido para él (por ejemplo: *10*).
1. En la página de edición del producto, abra **[!UICONTROL Advanced Inventory]**. Configure las variables **[!UICONTROL minimum quantity]** en el carro de compras, (por ejemplo: *160*). La cantidad debe estar por encima del inventario.
1. Vaya a la tienda y compre un producto para crear una reserva.
1. Cambie el **[!UICONTROL product quantity]** hasta *0*. El punto crítico es guardar el producto de **[!DNL Admin panel]** cuando hay una reserva.
1. Abra el **[!UICONTROL product page]** en la tienda e intente agregar el producto al carro de compras.

<u>Resultados esperados</u>:

Es posible añadir el producto al carro de compras porque hay pedidos pendientes de una cantidad inferior *0* están permitidas.

<u>Resultados reales</u>:

Se muestra que el producto está agotado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
