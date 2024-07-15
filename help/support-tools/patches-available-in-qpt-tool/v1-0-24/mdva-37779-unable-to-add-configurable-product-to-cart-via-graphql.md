---
title: "MDVA-37779: No se puede añadir un producto configurable al carro de compras mediante GraphQL"
description: El parche de MDVA-37779 Adobe Commerce soluciona el problema de que es imposible añadir un producto configurable al carro de compras cuando el ID del sitio web no es igual al ID de la tienda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. El ID del parche es MDVA-37779. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4. 
exl-id: 5f344896-39c3-4e17-89b8-1b987bae2968
feature: GraphQL, Configuration, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MDVA-37779: No se puede añadir un producto configurable al carro de compras mediante GraphQL

El parche de MDVA-37779 Adobe Commerce soluciona el problema de que es imposible añadir un producto configurable al carro de compras cuando el ID del sitio web no es igual al ID de la tienda. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. El ID del parche es MDVA-37779. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Es imposible añadir un producto configurable al carro de compras cuando el ID del sitio web no es igual al ID de la tienda.

<u>Requisitos previos</u>:

Tener un segundo sitio web, tienda y vista de tienda donde el ID del sitio web no sea igual al ID de la tienda.

<u>Pasos a seguir</u>:

1. Cree un carro vacío usando la mutación de GraphQl `createEmptyCart`.
1. Intente agregar un producto configurable al carro de compras usando la mutación `addConfigurableProductsToCart`.

<u>Resultados esperados</u>:

Producto añadido al carro de compras.

<u>Resultados reales</u>:

Obtener un error: *No se pudo agregar el producto con SKU xxxx al carro de compras: No se encontró el sitio web con el ID 3 solicitado. Compruebe el sitio web y vuelva a intentarlo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.


## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
