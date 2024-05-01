---
title: '"ACSD-48362: se utiliza la dirección de envío predeterminada en lugar de una nueva".'
description: Aplique el parche ACSD-48362 para solucionar el problema de Adobe Commerce en el que se utiliza la dirección de envío predeterminada en lugar de una nueva al realizar un pedido con una oferta negociable.
exl-id: 52f518b6-6f73-42cc-ac1b-c893cd5007fa
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-48362: se utiliza la dirección de envío predeterminada en lugar de una nueva

El parche ACSD-48362 corrige el problema en el que se utiliza la dirección de envío predeterminada en lugar de la dirección recién agregada al realizar un pedido utilizando una cotización negociable. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. El ID del parche es ACSD-48362. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se utiliza la dirección de envío predeterminada en lugar de la dirección de envío recién agregada al realizar un pedido con una oferta negociable.

<u>Pasos a seguir</u>:

1. Para activar el presupuesto B2B, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Inicie sesión como usuario de la empresa.
1. Añadir un producto al carro de compras.
1. Vaya a la página del carro de compras y solicite un presupuesto.
1. Vaya a la dirección del cliente **[!UICONTROL My Quotes]** y seleccione la oferta que acaba de crear.
1. Vaya a la **[!UICONTROL Shipping Information]** de la página de presupuesto del cliente.
   * Clic **[!UICONTROL Add New Address]**, rellene el formulario y guarde la dirección (no seleccione **[!UICONTROL Use as my default billing address]** o **[!UICONTROL Use as my default shipping address]**).
1. Clic **[!UICONTROL Send for Review]** en la página de presupuesto del cliente.
1. Vaya a Adobe Commerce Admin como usuario administrador, abra la oferta que acaba de crear y haga clic en **[!UICONTROL Send]**.
1. Ahora vaya a la página de presupuesto del cliente, actualice la página y haga clic en **[!UICONTROL Proceed to Checkout]**.
1. En la página de pago y envío, los datos muestran la dirección de envío predeterminada incluso cuando se selecciona la nueva dirección de envío.
1. Clic **[!UICONTROL Continue]** y realice el pedido.

<u>Resultados esperados</u>:

El pedido debe utilizar la nueva dirección sin volver a seleccionar la dirección de envío predeterminada en la página de cierre de compra.

<u>Resultados reales</u>:

El pedido se realiza con la dirección de envío predeterminada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube. 

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
