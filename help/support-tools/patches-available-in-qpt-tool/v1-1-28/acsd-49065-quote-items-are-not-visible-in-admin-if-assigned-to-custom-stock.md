---
title: "ACSD-49065: Los elementos de cotización no son visibles en el administrador"
description: Aplique el parche ACSD-49065 para corregir el problema de Adobe Commerce en el que los elementos de oferta no son visibles en el administrador si solo están asignados al stock personalizado.
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065: Los elementos de cotización no son visibles en el administrador

El parche ACSD-49065 corrige el problema en el que los elementos de cotización no son visibles en el administrador si solo están asignados al stock personalizado. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 está instalado. El ID del parche es ACSD-49065. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los elementos de oferta no son visibles en el administrador si solo se asignan al stock personalizado.

Requisitos previos:

**[!UICONTROL B2B]** y **[!UICONTROL Inventory]** deben estar instalados.

<u>Pasos a seguir</u>:

1. Activar **[!UICONTROL Company]** y **[!UICONTROL B2B Quote]** bajo **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Crear un secundario **[!UICONTROL Inventory Source]** y asignarlo a un secundario **[!UICONTROL Inventory Stock]**.
1. Crear un nuevo producto asignando solo el secundario (no predeterminado) **[!UICONTROL Inventory Source]**.
1. Vaya a la tienda y cree una nueva cuenta de empresa. Inicie sesión como **[!UICONTROL Company Admin]** y agregue el producto creado al carro de compras.
1. Vaya al carro de compras y *[!UICONTROL Request a Quote]*.
1. Vaya al administrador y vea la cotización solicitada en **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Resultados esperados</u>:

Los artículos son visibles en la nueva oferta creada con los nuevos productos sin volver a guardarlos.

<u>Resultados reales</u>:

El *[!UICONTROL Items Quoted]* La sección está vacía. Si vuelve a guardar el producto recién creado, los elementos aparecerán.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
