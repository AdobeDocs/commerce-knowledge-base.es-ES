---
title: Los métodos de pago no se muestran en el cierre de compra con varias direcciones
description: Este artículo explica que la mayoría de los métodos de pago no se muestran en el cierre de compra cuando se especifican varias direcciones de envío, ya que la funcionalidad solo se implementa para Cybersource.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Los métodos de pago no se muestran en el cierre de compra con varias direcciones

Este artículo explica que la mayoría de los métodos de pago no se muestran en el cierre de compra cuando se especifican varias direcciones de envío, ya que la funcionalidad solo se implementa para Cybersource.

## Productos y versiones afectados

* Adobe Commerce local 2.x.x
* Adobe Commerce en infraestructura en la nube 2.x.x

>[!NOTE]
>
>La integración principal de pagos de Adobe Commerce Cybersource está obsoleta desde la versión 2.3.3 y se eliminará completamente en la versión 2.4.0. Utilice el [extensión oficial](https://marketplace.magento.com/cybersource-global-payment-management.html) del mercado en su lugar.

## Problema

<u>Requisitos previos</u>: en el Administrador de Commerce, habilite y configure los métodos de pago de PayPal y Cybersource, y habilite el envío múltiple para su tienda.

<u>Pasos a seguir</u>:

1. En la tienda, agregue varios productos al carro de compras.
1. Vaya a la página del carro de compras.
1. Clic **Desproteger con varias direcciones**.
1. Inicie sesión o cree una cuenta.
1. Divida los productos entre las direcciones de la página Enviar a varias direcciones.
1. Clic **Ir a Información de envío**.
1. Seleccione los métodos de envío para cada envío.
1. Clic **Continuar a Información de facturación**.

<u>Resultado esperado</u>: PayPal y Cybersource están disponibles como opciones de pago.

<u>Resultado real</u>: solo Cybersource aparece como la opción de pago disponible.

## Causa

Actualmente, Cybersource es el único método de pago en vivo compatible para el pago multienvío, a partir de la versión 2.2.4. La compatibilidad con el envío múltiple probablemente se creará para cada método de pago uno por uno. Por el momento no se pueden proporcionar fechas exactas ni números de versión.
