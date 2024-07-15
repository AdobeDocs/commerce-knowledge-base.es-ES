---
title: "ACSD-46770: el correo electrónico de confirmación de pedido se envía incluso cuando [!UICONTROL Email Order Confirmation] está desmarcado"
description: Aplique el parche ACSD-46770 para corregir el problema de Adobe Commerce donde se envían correos electrónicos de confirmación de pedido incluso cuando [!UICONTROL Email Order Confirmation] no está seleccionado.
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770: el correo electrónico de confirmación de pedido se envía incluso cuando **[!UICONTROL Email Order Confirmation]** está desmarcado

El parche ACSD-46770 corrige el problema en el cual los pedidos se pueden realizar mediante la API de REST como usuario invitado incluso cuando **[!UICONTROL Email Order Confirmation]** no está seleccionado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. El ID del parche es ACSD-46770. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se envía un correo electrónico de confirmación de pedido aunque **[!UICONTROL Email Order Confirmation]** no esté seleccionado.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente.
1. Vaya a **[!UICONTROL Sales]** > **[!UICONTROL Order]** y haga clic en **[!UICONTROL Create New Order]**.
1. Seleccione el cliente, añada los productos al pedido, rellene la dirección y seleccione los métodos de envío y pago.
1. Antes de enviar el pedido, anule la selección de la casilla **[!UICONTROL Email Order confirmation]**.
1. Haga clic en **[!UICONTROL Submit Order]** para crear el pedido.

<u>Resultados esperados</u>:

No se debe enviar un correo electrónico de confirmación de pedido si se deselecciona **[!UICONTROL Email Order Confirmation]**.

<u>Resultados reales</u>:

Se enviará un correo electrónico de confirmación de pedido independientemente de la casilla de verificación **[!UICONTROL Email Order Confirmation]** sin seleccionar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
