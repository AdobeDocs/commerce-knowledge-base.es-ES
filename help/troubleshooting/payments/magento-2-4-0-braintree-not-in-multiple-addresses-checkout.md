---
title: 'Adobe Commerce 2.4.0: Braintree no está en el cierre de compra de varias direcciones'
description: Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 en el que los métodos de pago de Braintree no se incluyen al trabajar con el cierre de compra de varias direcciones. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%
---
# Adobe Commerce 2.4.0: Braintree no está en el cierre de compra de varias direcciones

Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 en el que los métodos de pago de Braintree no se incluyen al trabajar con el cierre de compra de varias direcciones. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.

Nota: Adobe Commerce recomienda usar la [extensión de Commerce Marketplace Braintree](https://marketplace.magento.com/paypal-module-braintree.html) para las versiones 2.3 y posteriores con el fin de mantener el cumplimiento de PSD. La extensión no ofrece la funcionalidad de cierre de compra de varias direcciones.

## Productos y versiones afectados

* Adobe Commerce local v2.4.0
* Adobe Commerce en infraestructura en la nube v2.4.0

## Problema

<u>Requisitos previos</u>:

Se utiliza la integración principal de Braintree.

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

Braintree está disponible como forma de pago.

<u>Resultado real</u>:

Braintree no está disponible como forma de pago.

## Solución

No habilite las opciones de varias direcciones si utiliza Braintree en Adobe Commerce 2.4.0. Este problema se solucionó en Adobe Commerce 2.4.1.
