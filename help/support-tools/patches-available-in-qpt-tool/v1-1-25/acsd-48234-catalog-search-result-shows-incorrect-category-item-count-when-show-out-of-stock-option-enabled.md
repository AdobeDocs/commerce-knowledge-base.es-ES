---
title: "ACSD-48234: resultado de la búsqueda en el catálogo recuento de elementos de categoría incorrecto cuando [!UICONTROL Display Out of Stock Products] está habilitado"
description: Aplique el parche ACSD-48234 para solucionar el problema de Adobe Commerce donde el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría cuando la opción [!UICONTROL Display Out of Stock Products] está habilitada.
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234: el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría **[!UICONTROL Display Out of Stock Products]** habilitados

El parche ACSD-48234 resuelve el problema en el que el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría cuando la opción **[!UICONTROL Display Out of Stock Products]** está habilitada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25. El ID del parche es ACSD-48234. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.


## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría cuando la opción **[!UICONTROL Display Out of Stock Products]** está habilitada.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y abra el atributo **[!UICONTROL color]**.
1. Añada dos opciones, por ejemplo, naranja y verde. Guarde el atributo.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** y agregue el atributo **[!UICONTROL color]** al conjunto de atributos **[!UICONTROL Default]**.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** y establezca **[!UICONTROL Display Out of Stock Products]** en _Sí_.
1. Crear categoría &quot;cat1&quot;.
1. Cree dos productos:
   1. Nombre: prod1, Color: orange, Categorías: cat1.
   1. Nombre: prod2, Color: green, Categorías: cat1.
1. Abra la categoría cat1 en la tienda.
1. Seleccione el color naranja en la navegación por capas.

<u>Resultados esperados</u>:

Solo se muestra el producto prod1.

<u>Resultados reales</u>:

Se muestran los productos prod1 y prod2.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
