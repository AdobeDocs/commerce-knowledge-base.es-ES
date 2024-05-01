---
title: '"Problema conocido de Adobe Commerce 2.4.0: falta la etiqueta "Reembolso" en Klarna"'
description: Este artículo proporciona una solución para un problema conocido en Administración para una etiqueta **Reembolso** que falta en Klarna VBE (extensión agrupada de proveedor). Cuando en el portal de Klarna se realiza un reembolso, la etiqueta **Reembolso** no se muestra junto al producto agrupado que se reembolsó.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.4.0: falta la etiqueta &quot;Reembolso&quot; en Klarna

Este artículo proporciona una solución para un problema conocido en Administración para un problema que falta **Reembolso** en Klarna VBE (extensión agrupada de proveedor). Cuando en el portal de Klarna que realiza un reembolso, la **Reembolso** La etiqueta no se muestra junto al producto agrupado que se reembolsó.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Requisitos previos:</u>

* Klarna está habilitado.
* Se crea un producto agrupado.

<u>Pasos a seguir</u>

1. Vaya al front-end de Adobe Commerce y añada un producto agrupado a **carrito**.
1. Vaya a Cierre de compra.
1. Introduzca la información del consumidor en el cierre de compra y haga clic en **Siguiente**.
1. Seleccionar **Opción KP** y haga clic en **Realizar pedido**.
1. Ir a **Administrador** > **Ventas** > **Pedidos**.
1. Abra el pedido.
1. Crear factura para el producto.
1. Ir a **Facturas** > **Seleccionar factura** > Haga clic **Nota de crédito** > Haga clic **Reembolso** (No **Reembolso sin conexión**).
1. Ve al portal Klarna.
1. Abra el pedido.
1. El **Reembolso** la etiqueta está presente.

<u>Resultado esperado</u>

En el portal Klarna, la **Reembolso** la etiqueta se muestra junto al producto que se ha reembolsado.

<u>Resultado real</u>

En el portal Klarna, la **Reembolso** la etiqueta no se muestra junto al producto que se ha reembolsado.

## Solución

La solución para este problema es ignorar lo que falta **Reembolso** etiqueta en el portal de Klarna para productos agrupados reembolsados. El reembolso se ha producido, aunque el **Reembolso** la etiqueta no se ha mostrado. Se espera que el problema se solucione en Adobe Commerce 2.4.1, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lecturas relacionadas en nuestra base de conocimiento de soporte:

* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensaje sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: Exportar tipos impositivos no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago del Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conocido de Adobe Commerce 2.4.0: error 404 al eliminar puntos de recompensa en el cierre de compra de envío múltiple](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: error de visualización de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conocido de creación de etiquetas de envío en Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
