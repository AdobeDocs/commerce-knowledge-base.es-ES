---
title: Problema conocido del recuento de productos de acción masiva en Adobe Commerce 2.3.5
description: En este artículo se describe un problema conocido de Adobe Commerce 2.3.5 en el que la notificación que recibe un comerciante tras una acción masiva en Administración contiene un número incorrecto de elementos afectados.
exl-id: 3ede15d4-4c39-442a-8784-2d5e6650fe67
feature: Products
role: Developer
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Problema conocido del recuento de productos de acción masiva en Adobe Commerce 2.3.5

En este artículo se describe un problema conocido de Adobe Commerce 2.3.5 en el que la notificación que recibe un comerciante tras una acción masiva en Administración contiene un número incorrecto de elementos afectados.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.3.5
* Adobe Commerce local 2.3.5

## Problema

El mensaje del sistema que muestra Adobe Commerce después de una acción masiva (por ejemplo, una actualización o importación/exportación masiva de productos) muestra un recuento de 0 en lugar de un recuento preciso de los productos afectados por la acción masiva.

## Fix

Habrá una corrección disponible en Adobe Commerce 2.3.6, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lectura relacionada

* Artículos de la Base de conocimiento de asistencia de Adobe Commerce para Adobe Commerce 2.3.5: Problemas conocidos:
   * [Los pedidos de envío múltiple con un producto virtual no se procesan correctamente en Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
   * [Problema conocido en Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
   * [Parche para el problema de cierre de compra de Amazon Pay en Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
   * [Problemas conocidos de Adobe Commerce 2.3.5 en nuestra documentación para desarrolladores](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
