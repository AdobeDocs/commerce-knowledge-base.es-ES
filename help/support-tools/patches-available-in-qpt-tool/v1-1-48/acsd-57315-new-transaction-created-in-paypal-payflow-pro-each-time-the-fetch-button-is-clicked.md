---
title: "ACSD-57315: la nueva transacción se crea en  [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón de recuperación"
description: Aplique el parche ACSD-57315 para corregir el problema de Adobe Commerce en el que se crea una nueva transacción en  [!DNL PayPal Payflow Pro]  cada vez que se hace clic en el botón de recuperación en la pantalla Ver transacción en [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
exl-id: bcc7467d-09f9-4235-9f9f-46d3034567b8
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón de recuperación

La revisión ACSD-57315 corrige el problema en el que se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón de recuperación en la pantalla Ver transacción en [!UICONTROL Admin]. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.48. El ID del parche es ACSD-57315. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón Recuperar en la pantalla Ver transacción en [!UICONTROL Admin].

<u>Pasos a seguir</u>:

1. Configurar [!DNL PayPal Payflow Pro].
1. Establezca el método de transacción en *[!UICONTROL Sale]*.
1. Haz un pedido con *tarjeta de crédito*.
1. Abra la transacción de [!UICONTROL Admin].
1. Haga clic en el botón **[!UICONTROL Fetch]**.
1. Compruebe la cuenta de [!DNL PayPal] para ver las transacciones relacionadas con el pedido realizado.

<u>Resultados esperados</u>:

No se crea una nueva transacción de pago.

<u>Resultados reales</u>:

Se crea una nueva transacción de pago para un pedido que ya se ha pagado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
