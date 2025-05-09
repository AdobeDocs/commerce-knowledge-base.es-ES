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

El parche ACSD-50949 corrige el problema en el que el filtro de precio en la búsqueda avanzada no devuelve los resultados adecuados cuando se utiliza junto con el filtro SKU. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. El ID del parche es ACSD-50949. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es>). Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

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

1. Abra **[!UICONTROL Advanced Search]** en la Tienda y busque por SKU: &quot;MJ&quot;.
1. Haga clic en el vínculo **[!UICONTROL Modify your search]**.
1. Agregue un rango de precios a los criterios de *1* a *21* y haga clic en el botón **[!UICONTROL Search]**.

<u>Resultados esperados</u>:

Solo se devuelven los productos con precios dentro del rango definido.

<u>Resultados reales</u>:

Se devuelven productos con precios superiores a *$21*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es>) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es>) en la guía [!DNL Quality Patches Tool].
