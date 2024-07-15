---
title: "ACSD-51379: Los cambios realizados en el contenido de texto de la página mediante  [!DNL Page Builder] no se guardan"
description: Aplique el parche ACSD-51379 para corregir el problema de Adobe Commerce en el que los cambios realizados en el contenido de texto de una página mediante  [!DNL Page Builder]  no se guardan.
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379: los cambios realizados en el contenido de texto de la página mediante [!DNL Page Builder] no se guardan

La revisión ACSD-51379 corrige el problema en el cual los cambios realizados en el contenido de texto de una página a través de [!DNL Page Builder] no se guardan. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32. El ID del parche es ACSD-51379. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los cambios realizados en el contenido de texto de una página mediante [!DNL Page Builder] no se guardarán.

<u>Pasos a seguir</u>:

1. Inicie sesión en Admin.
1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Cree una página de prueba con una fila y un elemento de texto en la ficha **[!UICONTROL Content]**.
1. Guarde la página y vuelva a la ficha **[!UICONTROL Content]**.
1. Edite el texto seleccionándolo y cambiándolo.

   **Nota:** El problema solo se puede reproducir si el texto se selecciona y se cambia sin activar el editor.

1. Haga clic en el botón **[!UICONTROL Save and Close]** de la página de prueba.
1. Vuelva a abrir la página de prueba y marque la ficha **[!UICONTROL Content]**.

<u>Resultados esperados</u>:

El nuevo texto se guarda correctamente para los elementos de texto originales y duplicados.

<u>Resultados reales</u>:

El elemento de texto se duplica correctamente, pero el nuevo texto no se guarda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
