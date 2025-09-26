---
title: La instalación de Adobe Commerce 2.4.0 falla con la memoria caché de tiendas obsoletas
description: 'Este artículo proporciona una solución para el problema en el que la instalación de Adobe Commerce 2.4.0 falla con el siguiente mensaje de error: * El sitio web predeterminado no está definido. Configure el sitio web e inténtelo de nuevo.* se muestra en la consola.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# La instalación de Adobe Commerce 2.4.0 falla con la memoria caché de tiendas obsoletas

Este artículo proporciona una solución para el problema en el que la instalación de Adobe Commerce 2.4.0 falla con el siguiente mensaje de error: *El sitio web predeterminado no está definido. Configure el sitio web e inténtelo de nuevo.* se muestra en la consola.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.0
* Adobe Commerce local 2.4.0

## Problema

<u>Requisitos previos:</u>
Una extensión de terceros con dependencias de API para el módulo Almacenar en comandos CLI se configura según se requiere en `composer.json`. Esto provoca que la instalación de Adobe Commerce 2.4.0 falle con un mensaje de error: *El sitio web predeterminado no está definido. Configure el sitio web e inténtelo de nuevo.* se muestra en la consola.

## Causa

El problema aparece para las extensiones de terceros que dependen de almacenes en sus comandos CLI. Una es los Canales de ventas de Amazon.

## Solución

Antes de la instalación de Adobe Commerce 2.4.0, los comerciantes deben:

1. Quite estas extensiones de terceros de `composer.json`.
1. Instalar Adobe Commerce sin extensiones.
1. Añada las extensiones después de la instalación.

Este problema se solucionará en la versión 2.4.1 de.

## Lecturas relacionadas en nuestra base de conocimiento de soporte:

* [Problema conocido de Adobe Commerce 2.4.0: falta la etiqueta &quot;Reembolso&quot; en Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Problema conocido de Adobe Commerce 2.4.0: faltan dos botones en la página Crear nuevo pedido en el administrador](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0, 2.4.1: Habilitar emisión de factura parcial de Braintree Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conocido de Adobe Commerce 2.4.0: Amazon Pay habilitado, faltan métodos de pago al volver al cierre de compra estándar utilizado](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)

