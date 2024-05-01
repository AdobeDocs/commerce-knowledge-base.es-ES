---
title: La búsqueda de SKU de MDVA-28357 en la página Búsqueda avanzada no funciona
description: El MDVA-28357 resuelve el problema en el que la búsqueda por SKU de producto en la página Búsqueda avanzada no lleva a que se muestre el producto correspondiente en los resultados de búsqueda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8. Tenga en cuenta que el problema se ha corregido en la versión 2.4.1 de Adobe Commerce.
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# La búsqueda de SKU de MDVA-28357 en la página Búsqueda avanzada no funciona

El MDVA-28357 resuelve el problema en el que la búsqueda por SKU de producto en la página Búsqueda avanzada no lleva a que se muestre el producto correspondiente en los resultados de búsqueda. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 está instalado. Tenga en cuenta que el problema se ha corregido en la versión 2.4.1 de Adobe Commerce.

## Productos y versiones afectados

* Este parche se ha diseñado para Adobe Commerce local 2.3.4-p2.
* El parche también es compatible con Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0 a 2.3.5-p2, y 2.4.0 a 2.4.0-p1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

En la búsqueda avanzada, al buscar con un SKU, se consulta el campo SKU con un comodín. Sin embargo, un comodín solo se puede utilizar con `sku.keyword`, para que esto no devuelva el producto esperado.

<u>Pasos a seguir</u>

1. Vaya a la página Búsqueda avanzada.
1. Busque por un número de SKU.

<u>Resultado real</u>

Se muestra el mensaje de error: *No se puede encontrar ningún elemento que coincida con estos criterios de búsqueda. Modifique la búsqueda*.

<u>Resultado esperado</u>

Se muestra un elemento de producto con un mensaje: *Se ha encontrado 1 elemento utilizando los siguientes criterios de búsqueda*  *SKU: XX-XXXX*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Aplicación de parches mediante la herramienta Parches de calidad](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
