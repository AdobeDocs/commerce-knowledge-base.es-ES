---
title: "ACSD-45168: URL compatibles con SEO no generadas para productos que tienen atributos url_key anulados"
description: Aplique el parche ACSD-45168 para corregir el problema de Adobe Commerce en el que las direcciones URL compatibles con SEO no se generan para los productos que tienen atributos url_key anulados en el nivel de vista de tienda.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168: URL compatibles con SEO no generadas para productos que tienen atributos url_key anulados

El parche ACSD-45168 soluciona el problema de que no se generan URL compatibles con SEO para los productos que tienen atributos url_key anulados en el nivel de vista de tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. El ID del parche es ACSD-45168. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las direcciones URL compatibles con SEO no se generan para los productos que tienen atributos url_key anulados en el nivel de vista de tienda.

<u>Pasos a seguir</u>:

1. Para establecer la configuración de la siguiente manera, vaya a **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Sí*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Sí*
1. Limpie la caché de configuración.
1. Cree dos categorías: [!UICONTROL Category 1] y [!UICONTROL Category 2].
1. Crear dos productos: [!UICONTROL Product 1] en [!UICONTROL Category 1], [!UICONTROL Product 2] en [!UICONTROL Category 1].
1. Cambie el ámbito a [!UICONTROL Default Store View] para [!UICONTROL Product 1].
1. Desmarque la dirección URL opcional [!UICONTROL Key] en [!UICONTROL Search Engine Optimization].
1. Guarde el producto.
1. Cambie a [!UICONTROL All Store Views].
1. Agregar [!UICONTROL Product 1] a [!UICONTROL Category 2] y agregar [!UICONTROL Product 2] a [!UICONTROL Category 2].
1. Marque la tabla [!UICONTROL url_rewrite] o [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Resultados esperados</u>:

La dirección URL compatible con SEO para [!UICONTROL Category 2] se ha creado para [!UICONTROL Product 1].

<u>Resultados reales</u>:

Falta la dirección URL compatible con SEO de [!UICONTROL Category 2] para [!UICONTROL Product 1] porque se sobrescribió el atributo de clave de URL para el ámbito de vista de tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
