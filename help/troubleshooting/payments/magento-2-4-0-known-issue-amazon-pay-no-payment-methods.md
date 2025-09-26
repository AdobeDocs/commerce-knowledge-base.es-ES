---
title: 'Problema conocido de Adobe Commerce 2.4.0: Amazon pay, sin métodos de pago'
description: Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 en el que faltan métodos de pago cuando los clientes utilizan **Volver al cierre de compra estándar**, después de habilitar Amazon Pay.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 60f68b9edabd13a69e84705b85d84fd10ee6e2be
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.4.0: Amazon pay, sin métodos de pago

Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 en el que faltan métodos de pago cuando los clientes usan **Volver al cierre de compra estándar**, una vez que han habilitado Amazon Pay.

## Productos y versiones afectados

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube v2.3.5.p1 y v2.4.0

<u>Pasos a seguir:</u>

1. Vaya a la tienda.
1. Añada cualquier elemento al carro de compras y continúe con el cierre de compra.
1. Inicie sesión en su cuenta de Amazon Pay.
1. Seleccione una dirección y continúe con el cierre de compra.
1. Haga clic en **Volver al cierre de compra estándar**.
1. Continúe con el cierre de compra.

<u>Resultados esperados:</u>

Los métodos de pago deben mostrarse después de reiniciar el cierre de compra.

<u>Resultados reales:</u>

Faltan métodos de pago.

## Solución

Se prevé una resolución para 2.4.1.

## Lecturas relacionadas en nuestra base de conocimiento de soporte:

* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
