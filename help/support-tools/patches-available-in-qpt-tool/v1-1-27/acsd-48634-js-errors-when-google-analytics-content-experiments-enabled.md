---
title: 'ACSD-48634: [!DNL JS] errores al [!DNL Google Analytics Content Experiments] enabled'
description: Aplique el parche ACSD-48634 para corregir [!DNL JS] errores en una [!DNL staging] actualizar página cuando [!DNL Google Analytics Content Experiments] está activada.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] errores al [!DNL Google Analytics Content Experiments] activado

Correcciones del parche ACSD-48634 [!DNL JS] errores en una [!DNL staging] actualizar página cuando [!DNL Google Analytics Content Experiments] está activada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. El ID del parche es ACSD-48634. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL JS] se producen errores en una [!DNL staging] actualizar página cuando [!DNL Google Analytics Content Experiments] está activada.

<u>Pasos a seguir</u>:

1. Entrada **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, cree un sitio web, una tienda y un sitio web adicionales **[!UICONTROL Store View]**. Asegúrese de que la **[!UICONTROL Store View]** es *[!UICONTROL Enabled]*.
1. Configurar **[!DNL Configure Google Analytics]** al ir a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
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
1. Deshabilitar **[!DNL Configure Google Analytics]** el **[!DNL Default Config]** [!DNL scope] al cambiar **[!UICONTROL Enable]** de *[!UICONTROL Yes]* hasta *[!UICONTROL No]*. ¡Asegúrate de no cambiar nada más!
1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Crear y editar cualquier **[!UICONTROL category]** y añada una actualización programada para él:
   * Cualquier nombre, fecha de inicio futura, fecha de finalización futura y cualquier cambio en **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Guarde la actualización y marque [!DNL browser developer console] para errores.

<u>Resultados esperados</u>:

No [!DNL JS] errores y los cambios en el [!DNL staging] la actualización se ha guardado correctamente.

<u>Resultados reales</u>:

[!DNL JS] Los errores de se pueden ver en la consola, el formulario no tiene el formato correcto y la variable [!DNL spinner] nunca se desactiva después de guardar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
