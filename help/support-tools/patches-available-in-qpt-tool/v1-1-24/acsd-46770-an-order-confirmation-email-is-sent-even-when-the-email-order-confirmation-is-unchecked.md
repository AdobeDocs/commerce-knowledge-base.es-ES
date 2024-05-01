---
title: '"ACSD-46770: el correo electrónico de confirmación de pedido se envía incluso cuando [!UICONTROL Email Order Confirmation] está desmarcada'''
description: Aplique el parche ACSD-46770 para corregir el problema de Adobe Commerce donde los correos electrónicos de confirmación de pedido se envían incluso cuando [!UICONTROL Email Order Confirmation] no está seleccionado.
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770: el correo electrónico de confirmación de pedido se envía incluso cuando **[!UICONTROL Email Order Confirmation]** está desmarcado

El parche ACSD-46770 corrige el problema en el que los pedidos se pueden realizar mediante la API de REST como usuario invitado incluso cuando **[!UICONTROL Email Order Confirmation]** no está seleccionado. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 está instalado. El ID del parche es ACSD-46770. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se envía un correo electrónico de confirmación de pedido incluso cuando **[!UICONTROL Email Order Confirmation]** no está seleccionado.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente.
1. Ir a **[!UICONTROL Sales]** > **[!UICONTROL Order]** y haga clic en  **[!UICONTROL Create New Order]**.
1. Seleccione el cliente, añada los productos al pedido, rellene la dirección y seleccione los métodos de envío y pago.
1. Antes de enviar el pedido, anule la selección del **[!UICONTROL Email Order confirmation]** casilla de verificación.
1. Haga clic en **[!UICONTROL Submit Order]** para crear el pedido.

<u>Resultados esperados</u>:

No se debe enviar un correo electrónico de confirmación de pedido si la variable **[!UICONTROL Email Order Confirmation]** no está seleccionado.

<u>Resultados reales</u>:

Se envía un correo electrónico de confirmación de pedido independientemente del no seleccionado **[!UICONTROL Email Order Confirmation]** casilla de verificación.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
