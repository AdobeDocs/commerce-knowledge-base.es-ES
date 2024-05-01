---
title: "MDVA-43491: La etiqueta de imagen base no se actualiza cuando se importa mediante CSV"
description: El parche MDVA-43491 soluciona el problema de que la `base_image_label` no se actualiza al importarla mediante un archivo CSV para un sitio web de varias tiendas. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. El ID del parche es MDVA-43491. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491: La etiqueta de imagen base no se actualiza cuando se importa mediante CSV

El parche MDVA-43491 corrige el problema en el que la variable `base_image_label` no se actualiza cuando se importa mediante un archivo CSV para un sitio web de varias tiendas. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalado. El ID del parche es MDVA-43491. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El `base_image_label` no se actualiza cuando se importa con un archivo CSV para un sitio web de varias tiendas.

<u>Requisitos previos</u>:

Uno o más sitios web, tiendas y vistas de tiendas existentes que no son predeterminados.

<u>Pasos a seguir</u>:

1. Cree un nuevo producto.

   * Cargue una imagen.
   * Asigne el producto a los sitios web recién creados.

1. Exporte el producto como CSV.
1. Actualice el `base_image_label` para cada vista de tienda, duplicando la fila predeterminada del archivo CSV.
1. Importe el archivo CSV. Actualizará correctamente las etiquetas de cada tienda, lo que se puede comprobar en la sección **Imágenes y vídeos** en la página de edición del producto.
1. Vuelva a exportar el archivo CSV y actualice el `base_image_label` con valores diferentes.
1. Vuelva a importar el archivo CSV.
1. Abra el producto en Admin y compruebe si la etiqueta se ha actualizado para cada vista de tienda.

<u>Resultados esperados</u>:

El texto alternativo (etiqueta de imagen) se actualiza con el valor específico del almacén según el archivo CSV.

<u>Resultados reales</u>:

El texto alternativo (etiqueta de imagen) no se actualiza con `base_image_label` en el archivo CSV.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
