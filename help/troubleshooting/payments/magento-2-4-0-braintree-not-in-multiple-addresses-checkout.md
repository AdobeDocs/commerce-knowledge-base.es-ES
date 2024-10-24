---
title: "Adobe Commerce 2.4.0: el Braintree no está en la comprobación de varias direcciones"
description: Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 en el que los métodos de pago del Braintree no se incluyen al trabajar con el cierre de compra de varias direcciones. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: el Braintree no está en el cierre de compra de varias direcciones

Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 en el que los métodos de pago del Braintree no se incluyen al trabajar con el cierre de compra de varias direcciones. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.

Nota: Adobe Commerce recomienda usar la [extensión de Braintree de Commerce Marketplace](https://marketplace.magento.com/paypal-module-braintree.html) para las versiones 2.3 y posteriores con el fin de mantener el cumplimiento de PSD. La extensión no ofrece la funcionalidad de cierre de compra de varias direcciones.

## Productos y versiones afectados

* Adobe Commerce local v2.4.0
* Adobe Commerce en infraestructura en la nube v2.4.0

## Problema

<u>Requisitos previos</u>:

Se utiliza la integración del Braintree principal.

<u>Pasos a seguir</u>:

1. Ve a la tienda.
1. Inicie sesión como cliente.
1. Añadir un producto al carro de compras.
1. Abra el carro de compras.
1. Pulse **Ver y editar carro**.
1. Presione **Desproteger con varias direcciones**.
1. Pulse **Ir a la información de envío**.
1. Pulse **Continuar con la información de facturación**.

<u>Resultado esperado</u>:

El Braintree está disponible como forma de pago.

<u>Resultado real</u>:

El Braintree no está disponible como forma de pago.

## Solución

No habilite las opciones de varias direcciones si utiliza Braintree en Adobe Commerce 2.4.0. Este problema se solucionó en Adobe Commerce 2.4.1.

## Lectura relacionada en nuestra base de conocimiento de soporte

* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensaje sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
