---
title: "Limpieza de direcciones de vértice: no se permiten direcciones diferentes"
description: Este artículo habla sobre la solución del problema en el que cuando el usuario intenta introducir una dirección de facturación y envío **diferente**, con la validación de direcciones de Vértice habilitada, la tienda no permite al usuario introducirla.
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Limpieza de direcciones de vértice: no se permiten direcciones diferentes

Este artículo habla sobre la solución del problema en el cual cuando el usuario intenta ingresar una dirección de facturación y envío **diferente**, con la validación de direcciones de Vértice habilitada, la tienda no permitirá que el usuario la ingrese.

## Productos y versiones afectados

* Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.5-p1

## Problema

<u>Pasos a seguir</u>:

1. Vaya a Administración > **Tiendas** > **Configuración** > **Ventas** > **Limpieza de direcciones**.
1. Seleccione *Habilitado* de la lista desplegable **Usar limpieza de direcciones de vértice** y **Guardar configuración**.
1. Vaya al front-end como invitado y añada un producto al carro de compras.
1. Haga clic en el icono Carro de compras y **Continuar con la compra**.
1. Rellene los campos de dirección.
1. Seleccione el **método de envío** deseado y haga clic en **Siguiente**.
1. Vuelve a hacer clic en el botón **Siguiente**.
1. Anule la selección de **Mis direcciones de facturación y envío** **son iguales** e introduzca una nueva dirección de facturación (diferente a Dirección).
1. Haga clic en el botón **Actualizar** y luego haga clic en **Actualizar dirección**.

<u>Resultados esperados</u>:

El usuario ve diferentes direcciones de facturación y envío.

<u>Resultados reales</u>:

Cuando el usuario pulsa Actualizar, las direcciones de facturación y envío vuelven a ser las mismas.

## Causa

Error de verificación de dirección de vértice.

## Solución

Deshabilite la verificación de direcciones de Vértice o actualice a 2.4.0.

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conocido de Adobe Commerce 2.4.0: error 404 al eliminar puntos de recompensa en el cierre de compra de envío múltiple](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: error de visualización de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago del Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de creación de etiquetas de envío en Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensaje sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: falta la etiqueta &quot;Reembolso&quot; en Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Problema conocido de Adobe Commerce 2.4.0: faltan dos botones en la página Crear nuevo pedido en el administrador](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Problema conocido de Adobe Commerce 2.4.0: cuando Braintree está habilitado, emisión de factura parcial de Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conocido de Adobe Commerce 2.4.0: Amazon Pay habilitado, faltan métodos de pago al volver al cierre de compra estándar utilizado](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problema conocido de Adobe Commerce 2.4.0: la instalación de 2.4.0 falla con la caché de tiendas obsoletas](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
