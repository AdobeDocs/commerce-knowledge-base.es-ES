---
title: "Problema conocido de Adobe Commerce 2.3.5: pedidos de varios envíos de productos virtuales"
description: En este artículo se explica un problema conocido de Adobe Commerce 2.3.5 por el que un pedido de envío múltiple que contiene un producto virtual no se procesa correctamente.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.3.5: pedidos de varios envíos de productos virtuales

En este artículo se explica un problema conocido de Adobe Commerce 2.3.5 por el que un pedido de envío múltiple que contiene un producto virtual no se procesa correctamente.

## Productos y versiones afectados

* Adobe Commerce local 2.3.5
* Adobe Commerce en infraestructura en la nube 2.3.5

## Problema

<u>Pasos a seguir</u>:

1. En la tienda, agregue productos físicos y virtuales al carro de compras.
1. Continúe con el cierre de compra y seleccione **Desproteger con varias direcciones**.
1. Añada toda la información necesaria y realice el pedido.

<u>Resultado esperado</u>:

Los pedidos de todos los productos se han realizado correctamente.

<u>Resultado real</u>:

El pedido del producto virtual está vacío.

## Fix

Habrá una corrección disponible en Adobe Commerce 2.3.6, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lectura relacionada

En nuestra base de conocimiento de soporte:

* [Problema conocido en Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Problema conocido del recuento de productos de acción masiva en Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Problema con el método de pago por país en Adobe Commerce 2.3.5 y 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce solicita a los clientes que inicien sesión, pero proporciona un vínculo no válido](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Parche para el problema de cierre de compra de Amazon Pay en Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

En nuestra documentación para desarrolladores:

* [Notas de la versión de Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
