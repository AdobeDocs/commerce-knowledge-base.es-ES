---
title: Problema de crédito de tienda durante el cierre de compra en Adobe Commerce 2.3.5
description: Este artículo proporciona una solución para el problema conocido relacionado con el crédito de la tienda durante el cierre de compra en Adobe Commerce 2.3.5, en el que los compradores obtienen errores durante el cierre de compra después de seleccionar y luego eliminar el uso del crédito de la tienda. Habrá disponible una corrección permanente en Adobe Commerce 2.3.6.
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: d51fd4d7b064b8eea6cd3771af279b74a8bdec48
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Problema de crédito de tienda durante el cierre de compra en Adobe Commerce 2.3.5

Este artículo proporciona una solución para el problema conocido relacionado con el crédito de la tienda durante el cierre de compra en Adobe Commerce 2.3.5, en el que los compradores obtienen errores durante el cierre de compra después de seleccionar y luego eliminar el uso del crédito de la tienda. Habrá disponible una corrección permanente en Adobe Commerce 2.3.6.

## Productos y versiones afectados

* Adobe Commerce local 2.3.5
* Adobe Commerce en infraestructura en la nube 2.3.5

## Problema

<u>Pasos a seguir</u>:

1. El cliente agrega productos al carro de compras y continúa con el cierre de compra.
1. El cliente especifica el crédito del almacén como forma de pago.
1. El cliente elimina el crédito del almacén y cambia el método de pago.
1. El cliente realiza el cierre de compra.

<u>Resultados esperados</u>:

Toda la información del pedido se muestra correctamente.

<u>Resultados reales</u>:

Adobe Commerce genera un error en la sección Resumen de pedidos de la página Pedidos.

## Solución

Los clientes pueden actualizar la página de pedidos, y la información del resumen de pedidos se cargará correctamente. Habrá una corrección disponible en Adobe Commerce 2.3.6, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lectura relacionada

Artículos sobre problemas conocidos de Adobe Commerce 2.3.5 en nuestra base de conocimiento de asistencia:

* [Los pedidos de envío múltiple con un producto virtual no se procesan correctamente en Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Problema con el método de pago por país en Adobe Commerce en la infraestructura en la nube y Adobe Commerce local 2.3.5 y 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)


* [Problema conocido del recuento de productos de acción masiva en Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Parche para el problema de cierre de compra de Amazon Pay en Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Problema de comparación de productos en Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

En nuestra documentación para desarrolladores:

* [Problemas conocidos de Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
