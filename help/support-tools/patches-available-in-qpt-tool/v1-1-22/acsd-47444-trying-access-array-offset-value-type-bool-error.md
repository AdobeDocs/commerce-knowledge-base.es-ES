---
title: "ACSD-47444: Error _[!UICONTROL Trying to access array offset on value of type bool]_ al acceder a determinadas rutas de categoría no existentes para productos conocidos en PHP 7.4"
description: Aplique el parche ACSD-47444 para corregir el problema de Adobe Commerce donde hay un error _[!UICONTROL Trying to access array offset on value of type bool]_ al acceder a ciertas rutas de categoría no existentes para productos conocidos, en PHP 7.4.
exl-id: dfe803d0-bcff-40e6-a759-8c2243235ea8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-47444: error _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;al acceder a determinadas rutas de categoría no existentes para productos conocidos en PHP 7.4

El parche ACSD-47444 resuelve el problema en el que se ve un error de _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;al acceder a ciertas rutas de categoría no existentes para productos conocidos en PHP 7.4. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Experimenta el siguiente error: _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;al acceder a ciertas rutas de categoría no existentes para productos conocidos, en PHP 7.4.

<u>Requisitos previos</u>:

PHP 7.4.

<u>Pasos a seguir</u>:

1. Cree un nuevo producto con el nombre &quot;test&quot;.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > conjunto **[!UICONTROL Generate "category/product" URL Rewrites]** = _No_.
1. Vaya a la tienda y visite la URL como ../abc/test.html (&quot;abc&quot; - no debería existir).

<u>Resultados esperados</u>:

404 páginas.

<u>Resultados reales</u>:

Error 500:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
