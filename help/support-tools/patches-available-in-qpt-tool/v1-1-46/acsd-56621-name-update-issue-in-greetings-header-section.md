---
title: "ACSD-56621: Los nombres actualizados no se muestran en el encabezado de saludos para el usuario administrador de la empresa"
description: Aplique el parche ACSD-56621 para solucionar el problema de Adobe Commerce donde el nombre y los apellidos actualizados del usuario administrador de la empresa no se reflejan en la sección del encabezado de saludos.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 4ad9c878-b617-4e6a-939c-be15faf7124b
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621: los nombres actualizados no se muestran en el encabezado de saludos para el usuario administrador de la empresa

El parche ACSD-56621 corrige el problema en el que el nombre y los apellidos actualizados del usuario administrador de la empresa no se reflejan en la sección del encabezado de saludos. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 está instalado. El ID del parche es ACSD-56621. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los nombres actualizados no se muestran en el encabezado de saludos para los usuarios administradores de la empresa.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Admin]** panel.
1. Ir a **[!UICONTROL Stores]** y seleccione **[!UICONTROL Configuration]**.
1. En el **[!UICONTROL General]** , seleccione **[!UICONTROL B2B]** para habilitar la funcionalidad de la empresa B2B.
1. Vaya a la **[!UICONTROL Storefront]** y registrar una nueva empresa.
1. Inicie sesión como usuario administrador de la empresa.
1. Ir a **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** y modifique los campos nombre y apellido según sea necesario.

<u>Resultados esperados</u>:

El nombre y los apellidos del usuario en la sección del encabezado de los saludos se cambian inmediatamente.

<u>Resultados reales</u>:

El nombre y los apellidos del usuario solo se cambian cuando este cierra la sesión y vuelve a iniciarla.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
