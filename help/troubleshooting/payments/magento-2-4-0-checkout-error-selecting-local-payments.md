---
title: 'Adobe Commerce 2.4.0: error de cierre de compra al seleccionar pagos locales'
description: 'Este artículo trata sobre una solución para un problema conocido en Adobe Commerce durante el cierre de compra, donde aparece un mensaje de error al seleccionar un método de pago local para algunos países. Esto ocurre en los siguientes países: Bélgica, Italia, Países Bajos, Polonia y España.'
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: error de cierre de compra al seleccionar pagos locales

Este artículo trata sobre una solución para un problema conocido en Adobe Commerce durante el cierre de compra, donde aparece un mensaje de error al seleccionar un método de pago local para algunos países. Esto ocurre en los siguientes países: Bélgica, Italia, Países Bajos, Polonia y España.

El mensaje de error &quot;*Actualmente no hay métodos de pago disponibles. Actualice la dirección de facturación.*&quot; aparecerá, pero los métodos de pago locales seguirán apareciendo y funcionando correctamente. Habrá disponible una corrección permanente en Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Requisitos previos</u>:

* Adobe Commerce 2.4.0 está instalado.
* Crear un producto y una categoría.
* Configurar [método de pago Braintree](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/).

<u>Pasos a seguir</u>:

1. Vaya a la tienda.
1. Seleccionar elementos para agregarlos al carro de compras.
1. Continúe con el cierre de compra.
1. Rellene el formulario de dirección con una dirección válida.
1. Acceda a la página Revisión y Pagos.

<u>Resultado esperado</u>:

Los métodos de pago locales deben mostrarse normalmente, sin mensaje de error.

<u>Resultado real</u>:

El mensaje de error &quot;*Actualmente no hay métodos de pago disponibles. Actualice la dirección de facturación.*&quot;, pero los métodos de pago locales seguirán mostrándose y funcionando correctamente.

## Solución

La solución es ignorar el mensaje de error mostrado y continuar con el pago como de costumbre, ya que todos los métodos de pago locales funcionarán normalmente. La corrección estaba disponible a partir de la versión 2.4.1 de Adobe Commerce.

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: Exportar tipos impositivos no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: la actualización de las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
