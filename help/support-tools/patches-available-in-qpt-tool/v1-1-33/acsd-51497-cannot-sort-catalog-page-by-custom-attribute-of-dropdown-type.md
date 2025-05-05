---
title: "ACSD-51497: No se puede ordenar la página del catálogo por atributo personalizado de tipo Desplegable"
description: Aplique el parche ACSD-51497 para solucionar el problema de Adobe Commerce en el que un cliente no puede ordenar una página de catálogo por atributo personalizado del tipo desplegable.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: 60a4f375-9b9a-4026-9dc7-d9f847a75656
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497: no se puede ordenar la página del catálogo por atributo personalizado de tipo *Desplegable*

El parche ACSD-51497 corrige el problema en el que un cliente no puede ordenar una página de catálogo por un atributo personalizado del tipo *Desplegable*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. El ID del parche es ACSD-51497. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un cliente no puede ordenar una página de catálogo por un atributo personalizado del tipo *Desplegable*.

<u>Pasos a seguir</u>

1. Cree unos seis productos simples y asígnelos a una sola categoría.
1. Cree un atributo de producto para añadirlo como opción de ordenación en las páginas de la lista.

   * Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * En la ficha **[!UICONTROL Properties]**, establezca lo siguiente:

      * *[!UICONTROL Default Label]* = *prueba*
      * *[!UICONTROL Catalog Input Type]* para propietario de tienda = *Menú desplegable*
      * *[!UICONTROL Options]*:

         * *primero*
         * *segundo*
         * *tercio*
         * *cuarto*

   * En la ficha **[!UICONTROL Storefront Properties]**, establezca lo siguiente:

      * *[!UICONTROL Used for sorting in product listing]* = *Sí*
      * Deje el resto de opciones como *Predeterminado*.

1. Asigne el atributo *test* al atributo *Default* establecido en **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Configure los productos para que tengan *test* valores de atributo.

   * SKU: s00001, prueba: cuarto
   * SKU: s00002, prueba: third
   * SKU: s00003, prueba: second
   * SKU: s00004, prueba: first
   * SKU: s00005, prueba: cuarto
   * SKU: s00006, prueba: third

1. Reindexe y borre la caché.
1. Vaya a la categoría de la tienda.
1. Ordenar por el atributo *test*.

<u>Resultados esperados</u>:

Los productos están ordenados por el atributo *test*.

<u>Resultados reales</u>:

Los productos no están ordenados por el atributo *test*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
