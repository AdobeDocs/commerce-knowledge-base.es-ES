---
title: '''ACSD-46617: **[!UICONTROL Continue to Checkout]** botón aparece en gris cuando el subtotal es mayor que la cantidad mínima de pedido configurada"'
description: Aplique el parche ACSD-46617 para resolver el problema de Adobe Commerce donde la **[!UICONTROL Continue to Checkout]** botón aparece en gris aunque el subtotal sea mayor que la cantidad mínima de pedido configurada.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: &quot;[!UICONTROL Continue to Checkout]El botón &quot; se atenuó cuando el subtotal era mayor que &quot;[!UICONTROL Minimum Order Amount]&quot;

Este parche de ACSD-46617 resuelve el problema en el que la variable **[!UICONTROL Continue to Checkout]** El botón aparece en gris aunque el subtotal sea mayor que la cantidad mínima de pedido configurada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 está instalado. El ID del parche es ACSD-46617. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El **[!UICONTROL Continue to Checkout]** El botón aparece en gris aunque el subtotal sea mayor que la cantidad mínima de pedido configurada.

<u>Pasos a seguir</u>:

1. Vaya a Adobe Commerce > Administración > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** y configure lo siguiente:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Crear un [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Cree un producto con el precio de 25 $.
1. Añadir el producto al carro de compras.
1. Vaya al carro de compras y seleccione la opción de 5 $ **[!UICONTROL Flat Rate shipping]** y aplique el código de cupón.
1. Vaya al cierre de compra, complete el envío y vaya al **[!UICONTROL Paytment]** sección.
1. Vuelva al carro de compras.

<u>Resultados esperados</u>:

No hay ningún error relacionado con la cantidad mínima del pedido, ya que el total general de 2,4 dólares es mayor que el importe requerido de 2 dólares.

<u>Resultados reales</u>:

* Hay un error relacionado con la cantidad mínima del pedido, incluso cuando el total general de 2,4 $ es mayor que la cantidad mínima del pedido de 2 $.
* El **[!UICONTROL Continue to Checkout]** El botón aparece atenuado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
