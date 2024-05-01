---
title: "ACSD-56280: Las compras en el registro de regalos no se han completado"
description: Aplique el parche ACSD-56280 para corregir el problema de Adobe Commerce en el que las compras del registro de regalos no se hayan completado
feature: Checkout
role: Admin
exl-id: 8e78ea1d-bd55-49d7-9d74-748b8f90e28c
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-56280: las compras en el registro de regalos no se han completado

El parche ACSD-56280 corrige el problema en el que las compras del registro de regalos no se completan. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. El ID del parche es ACSD-56280. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las compras del registro de regalos no se han completado.

<u>Pasos a seguir</u>:

1. Inicie sesión como cliente y añada una **[!UICONTROL product]** en el registro de regalos.
1. Comparta el vínculo del registro de regalos.
1. Abra el vínculo del registro de regalos en otra ventana del explorador o de incógnito.
1. Agregue la cantidad y agregue los artículos al carro de compras.
1. Vaya a la **[!UICONTROL Checkout Page]**, seleccione **[!UICONTROL shipping method]**(Como la dirección de envío ya está seleccionada, proporcionada por el solicitante de registro).
1. Seleccione el método de pago.
1. Haga clic en el botón Realizar pedido.

<u>Resultados esperados</u>:

Se debe realizar el pedido.

<u>Resultados reales</u>:

El pedido no se realiza y se muestra el siguiente error: `Call to a member function getUpdatedQty() on null`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
