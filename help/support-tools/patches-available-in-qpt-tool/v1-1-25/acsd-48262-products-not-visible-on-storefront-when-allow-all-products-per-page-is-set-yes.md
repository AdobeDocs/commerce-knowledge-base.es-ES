---
title: "ACSD-48262: productos no visibles en la tienda cuando [!UICONTROL Allow All Products Per Page] está establecido [!UICONTROL Yes]"
description: Aplique la revisión ACSD-48262 para corregir el problema de Adobe Commerce en el que los productos no son visibles en la tienda cuando la configuración de [!UICONTROL Allow All Products Per Page] está establecida en [!UICONTROL Yes].
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: productos no visibles en la tienda cuando [!UICONTROL Allow All Products Per Page] está establecido *[!UICONTROL Yes]*

La revisión ACSD-48262 corrige el problema en el que los productos no son visibles en la tienda cuando la configuración de [!UICONTROL Allow All Products Per Page] está establecida en *[!UICONTROL Yes]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25. El ID del parche es ACSD-48262. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La revisión ACSD-48262 corrige el problema en el que los productos no son visibles en la tienda cuando la configuración de [!UICONTROL Allow All Products Per Page] está establecida en *[!UICONTROL Yes]*.

<u>Pasos a seguir</u>:

1. Cree una categoría de prueba.
1. Cree un producto de prueba en la categoría de prueba.
1. Examine el producto para probar la página de categoría en la tienda y asegurarse de que el producto sea visible.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** y establezca la configuración de [!UICONTROL Allow All Products Per Page] en *[!UICONTROL Yes]*.
1. Borrar caché.
1. Comprueba la página de categoría en la tienda.

<u>Resultados esperados</u>:

El producto está visible.

<u>Resultados reales</u>:

El producto no es visible.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
