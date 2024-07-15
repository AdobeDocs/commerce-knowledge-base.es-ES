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

Este artículo proporciona una solución para un problema conocido en Adobe Commerce 2.4.0 por un error de página web &quot;*404 no encontrado*&quot; al eliminar puntos de recompensa en una página de pago de envío múltiple. Actualmente, en la página de pago multienvío, al intentar eliminar los puntos de recompensa que se usaron para pagar un pedido, se muestra una página &quot;*404 no encontrado*&quot; en lugar de la cancelación correcta de puntos de recompensa. Este problema se resolverá en con un parche de Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce 2.4.0 (todos los métodos de implementación)

## Problema

<u>Pasos a seguir</u>

1. Vaya a la tienda e inicie sesión como cliente.
1. Agregue al menos dos productos al **Carro de compras**.
1. Abra el **minicarrito**.
1. Haga clic en el vínculo **Ver y editar carro**.
1. Haga clic en el vínculo **Desproteger con varias direcciones**.
1. Seleccione las direcciones de envío en la página **Enviar a varias direcciones**.
1. Haz clic en el botón **Ir a la información de envío**.
1. Seleccione la **tarifa fija - Método de envío fijo** para cada dirección.
1. Haz clic en el botón **Continuar con la información de facturación**.
1. Marque la casilla **Usar sus puntos de recompensa** en la página **Información de facturación**.
1. Haz clic en el botón **Ir a revisar tu pedido**.
1. Haz clic en el vínculo **Eliminar** de cualquier dirección para eliminar los puntos de recompensa.

<u>Resultados esperados</u>

* Debería aparecer la página **Carro de compras**.
* El &quot;*Ha eliminado los puntos de recompensa de este pedido.Debería aparecer el mensaje*&quot;.

<u>Resultado real</u>

Aparece una página de error &quot;*404 no encontrado*&quot;.

## Solución

La solución consiste en hacer que el comprador vuelva al **carro** y elimine los puntos de recompensa de la página web del **carro**. Se espera que el problema se solucione en el parche de la versión 2.4.1 de Adobe Commerce, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensajes sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conocido de Adobe Commerce 2.4.0: error de visualización de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
