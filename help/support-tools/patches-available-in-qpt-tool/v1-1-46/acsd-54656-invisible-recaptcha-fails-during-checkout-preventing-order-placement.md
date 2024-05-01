---
title: Invisible [!DNL reCAPTCHA] falla durante la desprotección, lo que impide realizar un pedido
description: Aplique el parche ACSD-54656 para corregir el problema de Adobe Commerce donde la variable invisible [!DNL reCAPTCHA] no funciona correctamente durante el cierre de compra, lo que impide realizar un pedido.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656: invisible [!DNL reCAPTCHA] no funciona correctamente durante el cierre de compra, lo que impide realizar un pedido.

El parche ACSD-54656 corrige el problema en el que el [!DNL reCAPTCHA] no funciona correctamente durante el cierre de compra, lo que impide realizar un pedido. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 está instalado. El ID del parche es ACSD-54656. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Invisible [!DNL reCAPTCHA] no funciona correctamente durante el cierre de compra, lo que impide realizar un pedido.

<u>Pasos a seguir</u>:

1. Habilite cualquier tipo de [!DNL reCAPTCHA] para tarjeta regalo en el [!UICONTROL Checkout] página.
1. Añada el producto al carro de compras y vaya a **[!UICONTROL Checkout]** página.
1. Expanda el formulario de tarjeta de regalo y rellene un cupón de tarjeta de regalo válido.
1. Haga clic en **[!UICONTROL See balance and apply]** botón.

<u>Resultados esperados</u>:

La tarjeta regalo se ha aplicado correctamente.

<u>Resultados reales</u>:

Aparece el mensaje de error: *[!DNL reCAPTCHA]error de validación, vuelva a intentarlo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
