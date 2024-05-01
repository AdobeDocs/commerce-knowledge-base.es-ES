---
title: '''ACSD-51890: [!UICONTROL Submit review] se puede hacer clic en el botón varias veces"'
description: Aplique el parche ACSD-51890 para solucionar el problema de Adobe Commerce donde la variable [!UICONTROL Submit Review] se puede hacer clic varias veces sin [!DNL Google reCAPTCHA v3] validación.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: **[!UICONTROL Submit Review]** se puede hacer clic varias veces sin **[!DNL Google reCAPTCHA v3]** validación

>[!NOTE]
>
>Este parche se ha sustituido por [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

El parche ACSD-51890 corrige el problema en el que la variable **[!UICONTROL Submit Review]** se puede hacer clic varias veces sin **[!DNL Google reCAPTCHA v3]** validación. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 está instalado. El ID del parche es ACSD-51890. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El **[!UICONTROL Submit Review]** se puede hacer clic en el botón varias veces sin **[!DNL Google reCAPTCHA v3]** validación.

<u>Pasos a seguir</u>:

1. Activar **[!DNL Google reCAPTCHA v3]** para la revisión del producto.
1. Abra la página del producto y vaya a **[!UICONTROL Review]** y asegúrese de que la sección [!DNL reCAPTCHA] es visible.
1. Rellene el formulario de revisión y haga clic en **[!UICONTROL Submit Review]** botón varias veces lo más rápido posible.
1. Abra el **[!UICONTROL Review]** de la sección Administración.

<u>Resultados esperados</u>

No se crean revisiones duplicadas.

<u>Resultados reales</u>

Se crean revisiones duplicadas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
