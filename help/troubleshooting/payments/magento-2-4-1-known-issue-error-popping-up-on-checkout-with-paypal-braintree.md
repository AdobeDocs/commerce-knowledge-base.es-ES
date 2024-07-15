---
title: "Problema conocido de Adobe Commerce 2.4.1: aparece un error al cerrar la compra con el Braintree de PayPal"
description: En este artículo se describe un problema conocido de Adobe Commerce 2.4.1 en el que aparece un mensaje de error y desaparece en el paso Facturación del Pago y envío si se utiliza el pago del Braintree de PayPal y se ha seleccionado el envío de varias direcciones.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.4.1: aparece un error al cerrar la compra con el Braintree de PayPal

En este artículo se describe un problema conocido de Adobe Commerce 2.4.1 en el que aparece un mensaje de error y desaparece en el paso Facturación del Pago y envío si se utiliza el pago del Braintree de PayPal y se ha seleccionado el envío de varias direcciones.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube 2.4.1
* Adobe Commerce local 2.4.1

## Problema

Aparece un mensaje de error que desaparece en el paso Facturación del Pago y envío si se utiliza el pago al Braintree de PayPal y se ha seleccionado el envío de varias direcciones.

<u>Pasos a seguir:</u>

1. En la tienda, inicie sesión como cliente (si está habilitado en Administración, puede tratarse de un cierre de compra para invitados).
1. Añadir un producto al carro de compras.
1. Haga clic para abrir la previsualización del carro de compras.
1. Haga clic en **Ver y editar carro**.
1. En la página Carro de compras, haga clic en **Retirar con varias direcciones**.
1. Haga clic en **Ir a la información de envío** y especifique las direcciones.
1. Haga clic en **Continuar con la información de facturación**.
1. Seleccione **Braintree de PayPal** y haga clic en el botón **PayPal**.
1. En la ventana emergente, haz clic en **Aceptar y pagar**.

<u>Resultado esperado:</u>

El pedido se realiza sin ningún error.

<u>Resultado real:</u>

Se realiza el pedido, pero con un error. No se pudo inicializar el proceso de pago y envío de *PayPal. Póngase en contacto con el propietario de la tienda*.  el error se muestra durante un segundo y desaparece.

## Fix

Dado que la colocación del pedido no está bloqueada, no es necesario realizar pasos de solución.
