---
title: Problema conocido en Adobe Commerce 2.3.5
description: Este artículo contiene recomendaciones sobre cómo evitar un problema conocido de [comparación de productos](https://experienceleague.adobe.com/es/docs/commerce-admin/stores-sales/shopper-tools/product-compare) en Adobe Commerce local 2.3.5 y Adobe Commerce en la infraestructura en la nube 2.3.5.
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Problema conocido en Adobe Commerce 2.3.5

Este artículo proporciona recomendaciones sobre cómo evitar un problema conocido de [comparación de productos](https://experienceleague.adobe.com/es/docs/commerce-admin/stores-sales/shopper-tools/product-compare) en Adobe Commerce local 2.3.5 y Adobe Commerce en la infraestructura en la nube 2.3.5.

## Productos y versiones afectados

* Adobe Commerce local 2.3.5
* Adobe Commerce en infraestructura en la nube 2.3.5

## Problema

Cuando un usuario intenta comparar productos de diferentes vistas de tienda y un producto tiene un valor vacío para un atributo comparable, Adobe Commerce muestra una página de comparación de productos dañada.

## Solución

Especifique valores no vacíos para atributos de producto comparables o utilice el valor de vista de almacén predeterminado para el atributo. Los valores de atributo comparables no pueden estar vacíos.

>[!NOTE]
>
>Los atributos del producto están configurados para utilizarse en la comparación mediante la configuración **Comparable en tienda**. Para obtener más información, consulte [Creación de atributos de producto](https://experienceleague.adobe.com/es/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create#step-4-describe-the-storefront-properties) en nuestra guía del usuario.

Habrá una corrección disponible en Adobe Commerce 2.3.6, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

Puede ver la corrección en GitHub (tenga en cuenta que la corrección no se sometió a pruebas de regresión y no es una corrección rápida oficial): <https://github.com/magento/magento2/pull/27662>

## Lectura relacionada

<ul><li>Artículos de la Base de conocimiento de asistencia de Adobe Commerce para Adobe Commerce 2.3.5: Problemas conocidos:<ul>
<li>
<p title="Los pedidos de envío múltiple con un producto virtual no se procesan correctamente en Adobe Commerce 2.3.5"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">Los pedidos de envío múltiple con un producto virtual no se procesan correctamente en Adobe Commerce 2.3.5</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Problema conocido del recuento de productos de acción masiva en Adobe Commerce 2.3.5</a></li>
<li>
<p title="Parche para el problema de cierre de compra de Amazon Pay en Adobe Commerce 2.3.5-p1"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Parche para el problema de cierre de compra de Amazon Pay en Adobe Commerce 2.3.5-p1</a></p>
</li>
</ul>
</li><li><a href="https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues">Problemas conocidos de Adobe Commerce 2.3.5</a> en nuestra documentación para desarrolladores</li></ul>
