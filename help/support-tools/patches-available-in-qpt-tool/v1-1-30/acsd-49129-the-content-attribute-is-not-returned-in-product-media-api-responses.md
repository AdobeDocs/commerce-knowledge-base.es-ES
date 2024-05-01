---
title: '"ACSD-49129: Atributo "Contenido" no devuelto en las respuestas de API de medios del producto"'
description: Aplique el parche ACSD-49129 para corregir el problema de Adobe Commerce en el que el atributo *content* (*código de imagen base64*) no se devuelve en las respuestas de API de medios de producto rest/V1/products/sku/media.
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129: Atributo &quot;Contenido&quot; no devuelto en las respuestas de API de medios del producto

El parche ACSD-49129 corrige el problema en el que la variable *content* atributo (*[!UICONTROL base64 image code]*) no se devuelve en el `rest/V1/products/sku/media` respuestas de API de medios del producto. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.30 está instalado. El ID del parche es ACSD-49129. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El *content* atributo (*[!UICONTROL base64 image code]*) no se devuelve en el `rest/V1/products/sku/media` respuestas de API de medios del producto.

<u>Pasos a seguir</u>:

1. Cree un producto con una imagen.
1. Enviar *API DE GET REST* solicitud a `rest/V1/products/<sku>/media` y `rest/V1/products/<sku>/media/<entryId>`.
1. Compruebe las respuestas de la API.

<u>Resultados esperados</u>

El *content* con los datos está disponible mediante la API de REST.

<u>Resultados reales</u>

El *content* El atributo no está presente en las respuestas de API.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
