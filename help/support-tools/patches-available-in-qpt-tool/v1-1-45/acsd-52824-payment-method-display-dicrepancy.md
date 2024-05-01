---
title: "ACSD-52824: Métodos de pago desactivados mostrados para los clientes de la empresa"
description: Aplique el parche ACSD-52824 para solucionar el problema de Adobe Commerce donde [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] los métodos de pago aparecen para los clientes de la empresa a pesar de estar desactivados en la configuración de la empresa.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824: métodos de pago desactivados mostrados para los clientes de la empresa

El parche ACSD-52824 corrige el problema donde [!DNL PayPal Express], [!DNL Google Pay], y [!DNL Apple Pay] los métodos de pago aparecen para los clientes de la empresa a pesar de estar desactivados en la configuración de la empresa. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 está instalado. El ID del parche es ACSD-52824. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se muestran los métodos de pago desactivados para los clientes de la empresa.

<u>Pasos a seguir</u>:

1. Configuración y activación [!DNL PayPal Express Checkout]. Vaya a **[!UICONTROL Basic Settings]** > seleccionar **[!DNL PayPal Express Checkout]** y establezca la opción para **[!UICONTROL Display on Shopping Cart]** hasta *Sí*.
1. Configurar [!DNL Braintree] y habilitar [!DNL Apple Pay] y [!DNL Google Pay] mediante [!DNL Braintree].
1. Vaya a **[!UICONTROL Customers]** > **[!UICONTROL Companies]** y cree una nueva compañía.
1. Haga clic en **[!UICONTROL Advanced Settings]**, busque la variable **[!UICONTROL Applicable Payment Methods]** y elija **[!UICONTROL Selected Payment Methods]**.
1. En **[!UICONTROL Selected Payment Methods]**, elija los métodos de pago que están activados y no están asociados a *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]*, o *[!DNL Google Pay]*. Por ejemplo, seleccione **[!UICONTROL Check/Money Order]**.
1. Después de seleccionar los métodos de pago adecuados, cree un nuevo cliente y asócielo a la empresa creada anteriormente.
1. Inicie sesión con la cuenta de cliente asociada a la compañía y continúe para agregar artículos al carro de compras.
1. Preste atención al minicarrito, al carro de compras y al paso de pago durante el proceso de cierre de compra.

<u>Resultados esperados</u>:

Opciones de pago de [!DNL PayPal] y [!DNL Braintree] no son visibles en el minicarrito ni en el carro de compras.

<u>Resultados reales</u>:

Opciones de pago de [!DNL PayPal] y [!DNL Braintree] permanezca visible en el minicarrito y en el carrito de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
