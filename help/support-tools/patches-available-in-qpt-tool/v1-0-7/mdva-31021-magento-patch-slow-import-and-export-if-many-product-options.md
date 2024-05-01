---
title: "MDVA-31021: importación y exportación lentas si hay muchas opciones de producto"
description: El parche MDVA-31021 soluciona el problema cuando la importación/exportación tarda más de lo esperado con un gran número de opciones de productos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021: importación y exportación lentas si hay muchas opciones de producto

El parche MDVA-31021 soluciona el problema cuando la importación/exportación tarda más de lo esperado con un gran número de opciones de productos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalado.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.3.1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si hay 100 000 registros o más en el `catalog_product_option` , la validación del archivo de la función de importación/exportación tarda más de lo esperado. Antes de Importar/Exportar, para comprobar la validación de opciones, Adobe Commerce carga las opciones de producto de todos los productos existentes.

<u>Requisitos previos</u>:

Tienda Adobe Commerce con 5000 productos con opciones personalizadas. Cada producto debe tener al menos cuatro opciones personalizadas con dos o más opciones para elegir, de modo que haya 100 000 registros en `catalog_product_option` tabla.

<u>Pasos a seguir</u>:

1. Para un **Importar** ejemplo: cree un archivo de importación CSV con uno de los SKU del administrador de Commerce.
1. Añada cuatro opciones personalizadas al archivo de importación CSV.
1. Intente importar el archivo CSV desde el administrador de Commerce.

<u>Resultados esperados</u>:

La función Importar o Exportar se completa según lo esperado. La validación de un producto tarda menos de 10 segundos en completarse.

<u>Resultados reales</u>:

La función Importar o Exportar tarda más de lo esperado. La validación tarda más de 10 segundos en completarse con un solo producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
