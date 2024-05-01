---
title: "Adobe Commerce 2.4.2: El pago Venmo de Braintree no funciona"
description: En este artículo se describe un problema conocido de Adobe Commerce 2.4.2 en el que los pedidos no se generan al utilizar Venmo de Braintree durante el cierre de compra. No hay ninguna resolución disponible en este momento.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Adobe Commerce 2.4.2: el pago Venmo de Braintree no funciona

En este artículo se describe un problema conocido de Adobe Commerce 2.4.2 en el que los pedidos no se generan al utilizar Venmo de Braintree durante el cierre de compra. No hay ninguna resolución disponible en este momento.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.4.2

## Problema

<u>Condición previa</u> :

Habilitar pago Venmo en la configuración de Braintree.

<u>Pasos a seguir</u> :

1. En la tienda, agregue cualquier artículo al carro de compras.
1. Continúe en **Finalizar compra**.
1. Seleccione el método de envío adecuado.
1. Seleccionar **Venmo** como forma de pago.
1. Clic **Pagar con Venmo**.
1. Clic **Realizar pedido**.

<u>Resultados reales</u>:

El pedido no se crea en código Adobe Commerce después de que se redirija al cliente a la tienda desde la aplicación Venmo y no aparece ningún mensaje de error. El pedido se crea en el Braintree.

<u>Resultados esperados</u>:

El pedido se crea en Adobe Commerce después de que el cliente se redirija de nuevo a la tienda desde la aplicación Venmo y el pedido se crea en Braintree, según lo esperado.

## Solución

No hay ninguna resolución disponible en este momento.
