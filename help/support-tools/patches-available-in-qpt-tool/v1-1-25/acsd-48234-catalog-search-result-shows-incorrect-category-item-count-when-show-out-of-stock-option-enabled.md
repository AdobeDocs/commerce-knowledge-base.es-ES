---
title: 'ACSD-48234: resultado de la búsqueda en el catálogo recuento de elementos de categoría incorrecto al [!UICONTROL Display Out of Stock Products] enabled'
description: Aplique el parche ACSD-48234 para solucionar el problema de Adobe Commerce donde el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría cuando la variable [!UICONTROL Display Out of Stock Products] La opción está activada.
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234: el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría **[!UICONTROL Display Out of Stock Products]** activado

El parche ACSD-48234 resuelve el problema en el que el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría cuando la variable **[!UICONTROL Display Out of Stock Products]** La opción está activada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 está instalado. El ID del parche es ACSD-48234. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.


## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El resultado de la búsqueda en el catálogo muestra un recuento de elementos de categoría incorrecto cuando la variable **[!UICONTROL Display Out of Stock Products]** La opción está activada.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y abrir **[!UICONTROL color]** atributo.
1. Añada dos opciones, por ejemplo, naranja y verde. Guarde el atributo.
1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** y añada el **[!UICONTROL color]** atribuir a **[!UICONTROL Default]** conjunto de atributos.
1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** y establecer **[!UICONTROL Display Out of Stock Products]** hasta _Sí_.
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

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
