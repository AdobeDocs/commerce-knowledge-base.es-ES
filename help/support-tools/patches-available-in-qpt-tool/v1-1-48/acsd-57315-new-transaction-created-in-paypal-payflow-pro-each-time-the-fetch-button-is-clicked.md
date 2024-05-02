---
title: '''ACSD-57315: la nueva transacción se crea en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón fetch"'
description: Aplique el parche ACSD-57315 para solucionar el problema de Adobe Commerce en el que se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón fetch en la pantalla view transaction de la [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: la nueva transacción se crea en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón fetch

El parche ACSD-57315 corrige el problema en el que se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón fetch en la pantalla view transaction de la [!UICONTROL Admin]. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.48 está instalado. El ID del parche es ACSD-57315. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón fetch en la pantalla view transaction de la [!UICONTROL Admin].

<u>Pasos a seguir</u>:

1. Configurar [!DNL PayPal Payflow Pro].
1. Establezca el método de transacción en *[!UICONTROL Sale]*.
1. Realización de un pedido utilizando *Tarjeta de crédito*.
1. Abrir la transacción desde [!UICONTROL Admin].
1. Haga clic en **[!UICONTROL Fetch]** botón.
1. Marque [!DNL PayPal] cuenta para las transacciones relacionadas con el pedido realizado.

<u>Resultados esperados</u>:

No se crea una nueva transacción de pago.

<u>Resultados reales</u>:

Se crea una nueva transacción de pago para un pedido que ya se ha pagado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
