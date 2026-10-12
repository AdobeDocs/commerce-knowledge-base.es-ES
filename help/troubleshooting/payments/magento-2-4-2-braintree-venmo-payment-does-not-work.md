---
title: 'Adobe Commerce 2.4.2: el pago Venmo de Braintree no funciona'
description: Este artículo describe un problema conocido de Adobe Commerce 2.4.2 en el que los pedidos no se generan al utilizar Braintree Venmo durante el cierre de compra. No hay ninguna resolución disponible en este momento.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%
---
# Adobe Commerce 2.4.2: el pago Venmo de Braintree no funciona

Este artículo describe un problema conocido de Adobe Commerce 2.4.2 en el que los pedidos no se generan al utilizar Braintree Venmo durante el cierre de compra. No hay ninguna resolución disponible en este momento.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.4.2

## Problema

<u>Condición Previa</u> :

Habilite Venmo payment en la configuración de Braintree.

<u>Pasos a seguir</u> :

1. En la tienda, agregue cualquier artículo al carro de compras.
1. Continuar con **cierre de compra**.
1. Seleccione el método de envío adecuado.
1. Selecciona **Venmo** como forma de pago.
1. Haz clic en **Pagar con Venmo**.
1. Haga clic en **Realizar pedido**.

<u>Resultados reales</u>:

El pedido no se crea en código Adobe Commerce después de que se redirija al cliente a la tienda desde la aplicación Venmo y no aparece ningún mensaje de error. El pedido se crea en Braintree.

<u>Resultados esperados</u>:

El pedido se crea en Adobe Commerce después de que el cliente sea redirigido de nuevo a la tienda desde la aplicación Venmo y el pedido se crea en Braintree, según lo esperado.

## Solución

No hay ninguna resolución disponible en este momento.
