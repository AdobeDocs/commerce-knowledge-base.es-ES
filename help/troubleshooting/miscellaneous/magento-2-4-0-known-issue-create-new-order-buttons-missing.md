---
title: "Problema conocido de Adobe Commerce 2.4.0: faltan los botones Crear nuevo pedido"
description: Este artículo proporciona una solución alternativa para un problema conocido en el Administrador de Commerce de dos botones que faltan en la página de creación de pedidos. Al crear un pedido nuevo para un cliente nuevo o existente, no es posible añadir productos al pedido desde el catálogo, ya que faltan los botones **Añadir productos por SKU** y **Añadir productos**. Esto se debe a que el agrupamiento de JS está habilitado. Habrá una corrección disponible en Adobe Commerce 2.4.1.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.4.0: faltan los botones Crear nuevo pedido

Este artículo proporciona una solución alternativa para un problema conocido en el Administrador de Commerce de dos botones que faltan en la página de creación de pedidos. Al crear un pedido nuevo para un cliente nuevo o existente, no es posible añadir productos al pedido desde el catálogo ya que la variable **Añadir productos por SKU** y **Añadir productos** faltan botones. Esto se debe a que el agrupamiento de JS está habilitado. Habrá una corrección disponible en Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Pasos a seguir</u>

1. Ir a **Clientes > Todos los clientes**.
1. Haga clic en **Editar** vínculo de un cliente.
1. Haga clic en **Crear pedido** botón.

<u>Resultado esperado</u>

El **Añadir productos por SKU** y **Añadir productos** botones aparecen en la **Crear nuevo pedido** página.

<u>Resultado real</u>

El **Añadir productos por SKU** y **Añadir productos** faltan botones en la **Crear nuevo pedido** página.

## Solución

La solución a este problema es deshabilitar el paquete JS para la instancia de Adobe Commerce. Se espera que el problema se solucione en Adobe Commerce 2.4.1, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lecturas relacionadas en nuestra base de conocimiento de soporte

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
