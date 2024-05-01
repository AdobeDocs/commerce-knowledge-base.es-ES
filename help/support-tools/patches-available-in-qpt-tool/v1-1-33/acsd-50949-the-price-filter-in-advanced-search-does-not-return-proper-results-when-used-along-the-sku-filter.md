---
title: "ACSD-50949: El filtro de precio de la búsqueda avanzada no devuelve los resultados adecuados cuando se utiliza junto con el filtro SKU"
description: Aplique el parche ACSD-50949 para corregir el problema de Adobe Commerce en el que el filtro de precio en la búsqueda avanzada no devuelve los resultados adecuados cuando se utiliza junto con el filtro SKU.
feature: Orders, Search
role: Admin
exl-id: 3e1f88dc-07f6-4e10-b4b7-163648076cbc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# ACSD-50949: El filtro de precio en la búsqueda avanzada no devuelve los resultados adecuados cuando se utiliza con el filtro SKU

El parche ACSD-50949 corrige el problema en el que el filtro de precio en la búsqueda avanzada no devuelve los resultados adecuados cuando se utiliza junto con el filtro SKU. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 está instalado. El ID del parche es ACSD-50949. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Problema

El filtro de precio en la búsqueda avanzada no devuelve resultados adecuados cuando se utiliza junto con el filtro SKU.

<u>Pasos a seguir</u>:

1. Cree varios productos, por ejemplo:

   | SKU | Nombre | Precio | Cantidad |
   |-----|-----------|-------|----------|
   | MJ1 | Product 1 | 10 $ | 10 |
   | MJ2 | Product 2 | 15 $ | 10 |
   | MJ3 | Product 3 | 21 $ | 10 |
   | MJ4 | Product 4 | 32 $ | 10 |
   | MJ5 | Product 5 | 33 $ | 10 |
   | MJ6 | Product 6 | 34 $ | 10 |
   | MJ7 | Product 7 | 44 $ | 10 |

1. Abra el **[!UICONTROL Advanced Search]** en la Tienda y buscar por SKU: &quot;MJ&quot;.
1. Haga clic en **[!UICONTROL Modify your search]** vínculo.
1. Agregar un rango de precios a los criterios de *1* hasta *21* y haga clic en **[!UICONTROL Search]** botón.

<u>Resultados esperados</u>:

Solo se devuelven los productos con precios dentro del rango definido.

<u>Resultados reales</u>:

Productos con precios superiores a *21 $* se devuelven.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
