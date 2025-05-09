---
title: 'ACSD-48634: [!DNL JS] errores al [!DNL Google Analytics Content Experiments] habilitar'
description: Aplique el parche ACSD-48634 para corregir  [!DNL JS] errores en una página de actualización [!DNL staging] cuando [!DNL Google Analytics Content Experiments] esté habilitado.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] errores cuando [!DNL Google Analytics Content Experiments] está habilitado

La revisión ACSD-48634 corrige [!DNL JS] errores en una página de actualización de [!DNL staging] cuando [!DNL Google Analytics Content Experiments] está habilitado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. El ID del parche es ACSD-48634. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se producen [!DNL JS] errores en una página de actualización de [!DNL staging] cuando [!DNL Google Analytics Content Experiments] está habilitado.

<u>Pasos a seguir</u>:

1. En **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, cree un sitio web, una tienda y **[!UICONTROL Store View]** adicionales. Asegúrese de que **[!UICONTROL Store View]** sea *[!UICONTROL Enabled]*.
1. Para configurar **[!DNL Configure Google Analytics]**, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Para **[!DNL Main]** y sitios web adicionales [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* para otros campos, pero no los cambie.
   * Para **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Deshabilite **[!DNL Configure Google Analytics]** en **[!DNL Default Config]** [!DNL scope] cambiando **[!UICONTROL Enable]** de *[!UICONTROL Yes]* a *[!UICONTROL No]*. ¡Asegúrate de no cambiar nada más!
1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Cree y edite cualquier **[!UICONTROL category]** y agregue una actualización programada para él:
   * Cualquier nombre, fecha de inicio futura, fecha de finalización futura y cualquier cambio en **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Guarde la actualización y compruebe si hay errores en [!DNL browser developer console].

<u>Resultados esperados</u>:

No hay errores de [!DNL JS] y los cambios en la actualización de [!DNL staging] se guardaron correctamente.

<u>Resultados reales</u>:

[!DNL JS] errores están visibles en la consola, el formulario no tiene el formato correcto y [!DNL spinner] nunca se deshabilita después de guardar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
