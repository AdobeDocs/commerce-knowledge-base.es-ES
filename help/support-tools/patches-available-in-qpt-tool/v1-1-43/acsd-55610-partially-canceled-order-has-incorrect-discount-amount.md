---
title: "ACSD-55610: El pedido parcialmente cancelado tiene un importe de descuento incorrecto"
description: Aplique el parche ACSD-55610 para solucionar el problema de Adobe Commerce en el que un pedido parcialmente cancelado tiene un importe de descuento incorrecto.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: f4cca4fa-dc04-4c86-9176-c648b1d0e732
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-55610: el pedido parcialmente cancelado tiene un importe de descuento incorrecto

El parche ACSD-55610 soluciona el problema de los pedidos parcialmente cancelados que tienen un importe de descuento incorrecto. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.43 está instalado. El ID del parche es ACSD-55610. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un pedido parcialmente cancelado tiene un importe de descuento incorrecto.

<u>Pasos a seguir</u>:

1. Crear una regla de precios del carro de compras.

   * *[!UICONTROL Rule Name]*: *Rebajas de invierno*
   * *[!UICONTROL Active]* = *Sí*
   * *[!UICONTROL Websites]* = *Sitio web principal*
   * Seleccione todos los grupos de clientes.
   * Seleccione un cupón específico.
   * *[!UICONTROL Coupon Code]*: *WINTER10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Subtotal (excl. Tax) es igual o mayor que 75*
   * Aplicar *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *Sí*

1. Cree tres productos con los precios establecidos en 100.
1. Agregue los tres productos al carro de compras.
1. Aplique el cupón.
1. Realice el pedido.
1. Facturar un artículo del pedido y enviarlo.
1. Cancelar los otros dos elementos.
1. Compruebe la `base_discount_canceled` columna.

<u>Resultados esperados</u>:

El importe del descuento en `base_discount_cancelled` se refleja correctamente.

<u>Resultados reales</u>:

El `base_discount_cancelled` no es correcto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
