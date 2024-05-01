---
title: "Adobe Commerce 2.4.0: error 404 al eliminar los puntos de recompensa en el cierre de compra de envío múltiple"
description: Este artículo proporciona una solución para un problema conocido en Adobe Commerce 2.4.0 por un error de página web "*404 no encontrado*" al eliminar puntos de recompensa en una página de pago de envío múltiple. Actualmente, en la página de compra de envío múltiple, al intentar eliminar los puntos de recompensa que se utilizaron para pagar un pedido, se muestra una página "*404 no encontrado*" en lugar de la cancelación correcta de puntos de recompensa. Este problema se resolverá en con un parche de Adobe Commerce 2.4.1.
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: error 404 al eliminar los puntos de recompensa en el cierre de compra de envío múltiple

Este artículo proporciona una solución para un problema conocido en Adobe Commerce 2.4.0 para un &quot;*404 No encontrado*&quot;error de página web al eliminar puntos de recompensa en una página de pago de envío múltiple. Actualmente, en la página de pago multienvío, al intentar eliminar los puntos de recompensa que se utilizaban para pagar un pedido, un &quot;*404 No encontrado* Se muestra la página &quot; en lugar de la cancelación correcta de puntos de recompensa. Este problema se resolverá en con un parche de Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce 2.4.0 (todos los métodos de implementación)

## Problema

<u>Pasos a seguir</u>

1. Vaya a la tienda e inicie sesión como cliente.
1. Añada al menos dos productos a **Carro de compras**.
1. Abra el **Minicarrito**.
1. Haga clic en **Ver y editar el carro** vínculo.
1. Haga clic en **Desproteger con varias direcciones** vínculo.
1. Seleccione las direcciones de envío en la **Enviar a varias direcciones** página.
1. Haga clic en **Ir a Información de envío** botón.
1. Seleccione el **Tarifa plana: método de envío fijo** para cada dirección.
1. Haga clic en **Continuar a Información de facturación** botón.
1. Compruebe la **Use sus puntos de recompensa** de la casilla de verificación **Información de facturación** página.
1. Haga clic en **Ir a Revisar tu pedido** botón.
1. Haga clic en **Eliminar** para eliminar los puntos de recompensa.

<u>Resultados esperados</u>

* El **Carro de compras** página debería aparecer.
* El &quot;*Ha eliminado los puntos de recompensa de este pedido.* Debería aparecer el mensaje &quot;.

<u>Resultado real</u>

A &quot;*404 No encontrado* Aparece la página de error &quot;.

## Solución

La solución consiste en que el comprador vuelva al **Carrito** y eliminar los puntos de recompensa de la **Carrito** página web. Se espera que el problema se solucione en el parche de la versión 2.4.1 de Adobe Commerce, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensajes sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conocido de Adobe Commerce 2.4.0: error de visualización de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
