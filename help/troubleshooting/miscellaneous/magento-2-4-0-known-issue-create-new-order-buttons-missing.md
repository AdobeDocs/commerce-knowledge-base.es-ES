---
title: 'Problema conocido de Adobe Commerce 2.4.0: faltan los botones Crear nuevo pedido'
description: Este artículo proporciona una solución alternativa para un problema conocido en el Administrador de Commerce de dos botones que faltan en la página de creación de pedidos. Al crear un pedido nuevo para un cliente nuevo o existente, no es posible añadir productos al pedido desde el catálogo, ya que faltan los botones **Añadir productos por SKU** y **Añadir productos**. Esto se debe a que el agrupamiento de JS está habilitado. Habrá una corrección disponible en Adobe Commerce 2.4.1.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.4.0: faltan los botones Crear nuevo pedido

Este artículo proporciona una solución alternativa para un problema conocido en el Administrador de Commerce de dos botones que faltan en la página de creación de pedidos. Al crear un pedido nuevo para un cliente nuevo o existente, no es posible agregar productos al pedido desde el catálogo, ya que faltan los botones **Agregar productos por SKU** y **Agregar productos**. Esto se debe a que el agrupamiento de JS está habilitado. Habrá una corrección disponible en Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Pasos a seguir</u>

1. Vaya a **Clientes > Todos los clientes**.
1. Haga clic en el vínculo **Editar** de un cliente.
1. Haga clic en el botón **Crear pedido**.

<u>Resultado esperado</u>

Los botones **Agregar productos por SKU** y **Agregar productos** aparecen en la página **Crear nuevo pedido**.

<u>Resultado real</u>

Los botones **Agregar productos por SKU** y **Agregar productos** no aparecen en la página **Crear nuevo pedido**.

## Solución

La solución a este problema es deshabilitar el paquete JS para la instancia de Adobe Commerce. Se espera que el problema se solucione en Adobe Commerce 2.4.1, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lecturas relacionadas en nuestra base de conocimiento de soporte

* [Problema conocido de Adobe Commerce 2.4.0: Exportar tipos impositivos no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
