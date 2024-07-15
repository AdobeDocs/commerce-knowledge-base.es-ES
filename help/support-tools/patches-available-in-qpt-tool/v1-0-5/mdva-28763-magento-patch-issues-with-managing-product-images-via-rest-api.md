---
title: "MDVA-28763: problemas con la administración de imágenes de productos mediante la API de REST"
description: El parche MDVA-28763 resuelve varios problemas relacionados con la administración de la galería de medios mediante la API de REST. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Los problemas están programados para solucionarse en versiones posteriores de Adobe Commerce.
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763: problemas con la administración de imágenes de productos mediante la API de REST

El parche MDVA-28763 resuelve varios problemas relacionados con la administración de la galería de medios mediante la API de REST. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Los problemas están programados para solucionarse en versiones posteriores de Adobe Commerce (consulte las descripciones de los problemas en [Problemas](#issues).

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce local 2.3.2 - 2.3.3.x
* Adobe Commerce en infraestructura en la nube 2.3.2 - 2.3.3.x

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problemas {#issues}

El parche de MDVA-28763 incluye correcciones para los siguientes problemas asociados con la galería de medios:

* Cuando se usa la API de REST para actualizar vídeos de YouTube (`PUT rest/V1/products/ {SKU}`), Adobe Commerce muestra una miniatura del vídeo, pero el reproductor de vídeo no se carga cuando se hace clic en el botón &quot;Reproducir&quot;. Programado para corregirse en Adobe Commerce 2.3.6.
* `PUT /V1/products/:sku/media/:entryId` llamada crea una nueva entrada en lugar de reemplazar la existente. Corregido en Adobe Commerce 2.3.5.
* Problemas con la eliminación de imágenes de productos cuando los productos se asignan a varias vistas de tienda. Este problema se corrigió en Adobe Commerce 2.3.4.
* Los comerciantes con varios sitios web ahora pueden utilizar REST para crear y actualizar productos preservando al mismo tiempo la herencia de imágenes y funciones de imagen. Anteriormente, cuando un comerciante utilizaba REST para crear y actualizar productos y se actualizaba un producto para la vista de tienda, se cargaban y guardaban las funciones de imagen predeterminadas para esa vista de tienda. Como resultado, las funciones de imagen de vista de tienda dejaron de heredar del ámbito predeterminado después de la actualización. Programado para corregirse en Adobe Commerce 2.3.6.
* Atributos de medios (imagen, miniatura, ..) Los valores de las vistas de tienda que hacen referencia a imágenes eliminadas no se limpian automáticamente. Programado para corregirse en Adobe Commerce 2.4.2.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
