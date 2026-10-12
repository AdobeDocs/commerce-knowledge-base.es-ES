---
title: Los métodos de pago no se muestran en el cierre de compra con varias direcciones
description: Este artículo explica que la mayoría de los métodos de pago no se muestran en el cierre de compra cuando se especifican varias direcciones de envío, ya que la funcionalidad solo se implementa para Cybersource.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
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
source-wordcount: '262'
ht-degree: 0%
---
# Los métodos de pago no se muestran en el cierre de compra con varias direcciones

Este artículo explica que la mayoría de los métodos de pago no se muestran en el cierre de compra cuando se especifican varias direcciones de envío, ya que la funcionalidad solo se implementa para Cybersource.

## Productos y versiones afectados

* Adobe Commerce local 2.x.x
* Adobe Commerce en infraestructura en la nube 2.x.x

>[!NOTE]
>
>La integración principal de pagos de Adobe Commerce Cybersource está obsoleta desde la versión 2.3.3 y se eliminará completamente en la versión 2.4.0. En su lugar, use la [extensión oficial](https://marketplace.magento.com/cybersource-global-payment-management.html) del mercado.

## Problema

<u>Requisitos previos</u>: en el administrador de Commerce, habilita y configura los métodos de pago de PayPal y Cybersource, y habilita el envío múltiple para tu tienda.

<u>Pasos a seguir</u>:

1. En la tienda, agregue varios productos al carro de compras.
1. Vaya a la página del carro de compras.
1. Haga clic en **Desproteger con varias direcciones**.
1. Inicie sesión o cree una cuenta.
1. Divida los productos entre las direcciones de la página Enviar a varias direcciones.
1. Haga clic en **Ir a la información de envío**.
1. Seleccione los métodos de envío para cada envío.
1. Haga clic en **Continuar con la información de facturación**.

<u>Resultado esperado</u>: PayPal y Cybersource están disponibles como opciones de pago.

<u>Resultado real</u>: Solo Cybersource aparece como la opción de pago disponible.

## Causa

Actualmente, Cybersource es el único método de pago en vivo compatible para el pago multienvío, a partir de la versión 2.2.4. La compatibilidad con el envío múltiple probablemente se creará para cada método de pago uno por uno. Por el momento no se pueden proporcionar fechas exactas ni números de versión.
