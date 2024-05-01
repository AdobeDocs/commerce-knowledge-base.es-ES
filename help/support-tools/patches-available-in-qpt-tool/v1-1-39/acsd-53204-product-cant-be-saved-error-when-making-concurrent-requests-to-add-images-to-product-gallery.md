---
title: "ACSD-53204: * El producto no se puede guardar * error en solicitudes simultáneas para agregar imágenes a la galería"
description: Aplique el parche ACSD-53204 para corregir el problema de Adobe Commerce en el que se produce el error *El producto no se puede guardar* al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante el punto final rest/V1/products/&lt;sku&gt;/media.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204: &quot;*No se puede guardar el producto*&quot;error en solicitudes simultáneas para agregar imágenes a la galería

El parche ACSD-53204 corrige el problema donde &quot;*No se puede guardar el producto* Se genera el error &quot; al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante `rest/V1/products/<sku>/media` punto final. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.39 está instalado. El ID del parche es ACSD-53204. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

&quot;*No se puede guardar el producto* Se genera el error &quot; al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante `rest/V1/products/<sku>/media` punto final.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel de administración.
1. Cree un producto con el SKU p1.
1. Realice varias solicitudes simultáneas a la `rest/V1/products/<sku>/media` punto final para cargar varias imágenes simultáneamente.

<u>Resultados esperados</u>:

Las imágenes se guardan sin errores.

<u>Resultados reales</u>:

&quot;*No se puede guardar el producto*&quot;El error se devuelve de vez en cuando.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
