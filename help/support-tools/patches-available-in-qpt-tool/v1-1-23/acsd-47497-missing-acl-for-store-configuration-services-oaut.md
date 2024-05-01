---
title: 'ACSD-47497: falta ACL para almacenamiento/configuración/servicios [!UICONTROL OAuth]'
description: Aplique el parche ACSD-47497 para solucionar el problema de Adobe Commerce cuando los permisos están configurados para una función en particular y no puede definir el acceso a la sección de configuración.
exl-id: c13fd541-1379-4893-9190-9da1422b2b99
feature: Configuration, Identity Management, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-47497: falta ACL para almacenamiento/configuración/servicios [!UICONTROL OAuth]

El parche ACSD-47497 resuelve el problema en el que la variable **[!UICONTROL Services]** La pestaña no es visible en **[!UICONTROL Configuration]** de la sección Administración de Adobe Commerce. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 está instalado. El ID del parche es ACSD-47497. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando los permisos se establecen para una función en particular, no se puede definir el acceso a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de Adobe Commerce. Ir a **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Seleccionar **[!UICONTROL Role Resources]** en la función Administradores y establezca **[!UICONTROL Resource Access]** bajo **[!UICONTROL Roles Resources]** hasta _Personalizado_, a continuación, active todas las casillas de verificación. Seleccionar **[!UICONTROL Save Role]**.
1. Seleccionar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**. El **[!UICONTROL OAuth]** La sección de configuración de no está disponible.

<u>Resultados esperados</u>:

Entrada **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, la sección de configuración está visible.

<u>Resultados reales</u>:

Entrada **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** No obstante, falta la sección de configuración.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
