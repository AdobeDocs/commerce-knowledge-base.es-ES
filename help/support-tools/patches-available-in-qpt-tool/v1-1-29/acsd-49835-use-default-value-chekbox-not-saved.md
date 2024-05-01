---
title: '''ACSD-49835: [!UICONTROL Use Default Value] la casilla de verificación no está guardada"'
description: Aplique el parche ACSD-49835 para solucionar el problema de Adobe Commerce donde la variable [!UICONTROL Use Default Value] La casilla de verificación no se guarda correctamente en un nivel de tienda para un atributo de selección múltiple.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835: [!UICONTROL Use Default Value] La casilla de verificación no está guardada

El parche ACSD-49835 corrige el problema en el que la variable [!UICONTROL Use Default Value] La casilla de verificación no se guarda correctamente en un nivel de tienda para un atributo de selección múltiple. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-49835. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El [!UICONTROL Use Default Value] La casilla de verificación no se guarda correctamente en un nivel de tienda para un atributo de selección múltiple.

<u>Pasos a seguir</u>:

1. Crear un **[!UICONTROL Multiple-select Attribute]** in **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y añadirlo a un conjunto de atributos.
1. Vaya a **[!UICONTROL Product]** y guardar **[!UICONTROL Values]** in **[!UICONTROL All Store Views (Default Scope)]**.
1. Ir a un específico **[!UICONTROL Store View Scope]** y guarde el producto.
1. Ir a **[!UICONTROL Store View Scope]** y compruebe la **[!UICONTROL Use Default Value]** casilla de verificación

<u>Resultados esperados</u>:

Los valores de atributos de selección múltiple se guardan correctamente al comprobar la [!UICONTROL Use Default Value] casilla de verificación en la [!UICONTROL Store View Scope].

<u>Resultados reales</u>:

Los valores de atributos de selección múltiple no se guardan correctamente al comprobar la [!UICONTROL Use Default Value] casilla de verificación en la [!UICONTROL Store View Scope].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
