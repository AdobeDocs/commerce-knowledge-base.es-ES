---
title: "ACSD-49835: la casilla de verificación [!UICONTROL Use Default Value] no se ha guardado"
description: Aplique el parche ACSD-49835 para corregir el problema de Adobe Commerce en el que la casilla de verificación [!UICONTROL Use Default Value] no se guarda correctamente en un nivel de almacén para un atributo de selección múltiple.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835: la casilla de verificación [!UICONTROL Use Default Value] no se ha guardado

El parche ACSD-49835 corrige el problema en el que la casilla de verificación [!UICONTROL Use Default Value] no se guarda correctamente en un nivel de almacén para un atributo de selección múltiple. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. El ID del parche es ACSD-49835. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La casilla de verificación [!UICONTROL Use Default Value] no se ha guardado correctamente en un nivel de almacén para un atributo de selección múltiple.

<u>Pasos a seguir</u>:

1. Cree un(a) **[!UICONTROL Multiple-select Attribute]** en **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y agréguelo a un conjunto de atributos.
1. Vaya a **[!UICONTROL Product]** y guarde **[!UICONTROL Values]** en **[!UICONTROL All Store Views (Default Scope)]**.
1. Vaya a un(a) **[!UICONTROL Store View Scope]** específico(a) y guarde el producto.
1. Vaya a **[!UICONTROL Store View Scope]** y marque la casilla **[!UICONTROL Use Default Value]**.

<u>Resultados esperados</u>:

Los valores de atributos de selección múltiple se guardan correctamente al marcar la casilla de verificación [!UICONTROL Use Default Value] en [!UICONTROL Store View Scope].

<u>Resultados reales</u>:

Los valores de atributos de selección múltiple no se guardaron correctamente al marcar la casilla de verificación [!UICONTROL Use Default Value] en [!UICONTROL Store View Scope].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
