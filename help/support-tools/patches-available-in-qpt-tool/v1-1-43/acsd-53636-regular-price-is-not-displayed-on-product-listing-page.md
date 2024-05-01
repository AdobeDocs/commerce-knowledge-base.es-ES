---
title: '"ACSD-53636: El precio normal no se muestra en [!UICONTROL Product Listing] page'''
description: Aplique el parche ACSD-53636 para corregir el problema de Adobe Commerce en el que el precio normal no se muestra en *[!UICONTROL Product Listing]* páginas para productos configurables que tienen productos secundarios con precios especiales.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636: el precio normal no se muestra en *[!UICONTROL Product Listing]* página

El parche ACSD-53636 soluciona el problema de que el precio normal no aparece en *[!UICONTROL Product Listing]* páginas para productos configurables que tienen productos secundarios con precios especiales. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 está instalado. El ID del parche es ACSD-53636. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio normal no aparece en *[!UICONTROL Product Listing]* páginas para productos configurables que tienen productos secundarios con precios especiales.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de y vaya a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** y cree o abra cualquier producto configurable.
2. Abra el producto secundario y agregue un precio especial a todos o a uno de los productos secundarios y guarde el producto.
3. Vaya a front-end y abra el **[!UICONTROL Product Detail]** página del producto configurable; en las muestras del producto secundario con precio especial, verá el *[!UICONTROL Regular price]* tachado (esperado).
4. Vaya a front-end y abra el **[!UICONTROL Product Listing]** página para el producto configurable con precio especial; compruebe que los cambios de muestra del producto configurable no muestren el precio normal, a diferencia del *[!UICONTROL Product Detail Page]* y otros productos simples.

<u>Resultados esperados</u>:

En el *[!UICONTROL Product Listing]* , el producto configurable muestra el precio normal de su producto secundario.

<u>Resultados reales</u>:

En el *[!UICONTROL Product Listing]* , el producto configurable no muestra el precio normal para su producto secundario.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
