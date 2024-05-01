---
title: "MDVA-37082: Índice parcial incorrecto del estado de las existencias para los productos agrupados"
description: El parche del Magento MDVA-37082 corrige el problema cuando el índice parcial del estado de las existencias de los productos agrupados es incorrecto para las existencias personalizadas. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. El ID del parche es MDVA-37082. Tenga en cuenta que el problema está programado para solucionarse en el Magento 2.4.4.
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082: Índice parcial incorrecto del estado de las existencias para productos agrupados

El parche del Magento MDVA-37082 corrige el problema cuando el índice parcial del estado de las existencias de los productos agrupados es incorrecto para las existencias personalizadas. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalado. El ID del parche es MDVA-37082. Tenga en cuenta que el problema está programado para solucionarse en el Magento 2.4.4.


## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
Adobe Commerce en infraestructura en la nube 2.3.4-p2

**Compatible con las versiones de Adobe Commerce:**
Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0-2.4.2-p1
>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La indexación incremental de productos secundarios de productos agrupados puede provocar que otros productos agrupados incorrectos se indexen incorrectamente cuando se comparten productos secundarios.

<u>Pasos a seguir</u>:

* Cree un nuevo inventario y un nuevo origen para el sitio web principal.
* Cree 3 productos simples con la cantidad 10, 15 y 0.
* Cree 2 productos agrupados y pase el primer producto simple con una cantidad de 10 a uno y otros 2 productos simples al otro.
* Confirme que ambos productos agrupados pueden ser accesibles desde el front-end, en stock.
* Asigne el producto simple con la cantidad 0 a los primeros productos de promoción de ventas agrupados.
* Limpie la caché de página completa y compruebe el segundo producto agrupado desde el front-end.
* Ejecute un reindexado completo.
* Compruebe el segundo producto agrupado del front-end.
* Guarde el primer producto agrupado.
* Limpie la caché de página completa y compruebe el segundo producto agrupado desde el front-end.

<u>Resultados esperados</u>:

El producto agrupado no está agotado después de guardar otro producto agrupado con ampliación de venta. El problema se resuelve después de un reindexado completo.

<u>Resultados reales</u>:

El segundo producto agrupado se queda sin existencias al guardar el primer producto agrupado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos a nuestra documentación para desarrolladores, según el método de implementación de Adobe Commerce:

* Adobe Commerce local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Comprobar si el parche está disponible para el problema del Magento mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
