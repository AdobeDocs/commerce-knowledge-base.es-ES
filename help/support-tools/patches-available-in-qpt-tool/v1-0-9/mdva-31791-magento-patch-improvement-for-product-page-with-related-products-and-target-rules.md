---
title: "MDVA-31791 patch: mejora de la página del producto con productos relacionados y reglas de Target"
description: El parche MDVA-31791 mejora el rendimiento de las páginas de producto cuando se utilizan [productos relacionados](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) o [reglas de productos relacionados](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (reglas de destino). Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# Parche MDVA-31791: mejora de la página de productos con productos relacionados y reglas de segmentación

El parche MDVA-31791 mejora el rendimiento de las páginas de productos cuando [Productos relacionados](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) o [Reglas de productos relacionados](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (reglas de target). Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.0

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube y Adobe Commerce local 2.3.4, 2.3.4-p1, 2.3.4-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Rendimiento bajo de las páginas de productos si se utilizan productos relacionados o reglas de Target.

Considere aplicar el parche MDVA-31791 si va a usar [Producto relacionado](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) o [Reglas de producto relacionadas](https://docs.magento.com/user-guide/marketing/product-related-rules.html) funcionalidad.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
