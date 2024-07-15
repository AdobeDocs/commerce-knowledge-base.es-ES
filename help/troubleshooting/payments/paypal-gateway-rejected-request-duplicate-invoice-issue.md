---
title: 'Solicitud rechazada de puerta de enlace de PayPal: emisión de factura duplicada'
description: 'Este artículo proporciona una corrección para la solicitud rechazada de puerta de enlace de PayPal: emisión de factura duplicada.'
exl-id: b6c4ede1-97a5-4db3-9b05-ab979cf809b3
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Solicitud rechazada de puerta de enlace de PayPal: emisión de factura duplicada

Este artículo proporciona una corrección para la solicitud rechazada de puerta de enlace de PayPal: emisión de factura duplicada.

Al enviar el pago, los clientes pueden ver un error en una factura duplicada:

>La puerta de enlace de PayPal ha rechazado la solicitud. Ya se ha realizado el pago de este ID de factura (\#10412: Duplicar factura)

El problema se produce cuando las facturas con los mismos ID se envían a PayPal varias veces.

Para resolver el problema, permite varios pagos por ID de factura en las Preferencias de recepción de pagos de PayPal. Cuando se cambia, PayPal acepta pagos sin mensajes de error, incluso para facturas con ID duplicados.

## Versiones afectadas

* Adobe Commerce local, todas las versiones
* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

Al enviar el pago, los clientes ven el siguiente mensaje de error:

```
... main.CRITICAL: Exception message: PayPal gateway has rejected request. Payment has already been made for this InvoiceID (#10412: Duplicate invoice).
```

PayPal no puede procesar el pago y completar el pedido.

## Causa

El mensaje de error se muestra cuando las facturas con el mismo identificador se envían a PayPal varias veces.

Esto puede ocurrir cuando se utilizan las mismas credenciales en varios sitios de Adobe Commerce (incluso en los entornos Local y de Ensayo). Los escenarios particulares pueden ser los siguientes:

* Varias tiendas envían facturas a PayPal y utilizan los mismos ID de factura
* Un nuevo almacén envía una factura con un ID que un almacén antiguo ha enviado anteriormente

De forma predeterminada, PayPal no permite procesar la misma factura dos veces.

## Solución

Cambia tu perfil de PayPal para permitir varios pagos por identificador de factura. Debes realizar estos cambios a través de PayPal.

1. Inicie sesión en su cuenta en [https://www.paypal.com](https://www.paypal.com/).
1. Haga clic en **Perfil** > **Perfil y configuración** (esquina superior derecha).
1. Ve a **Mis herramientas de venta**.
1. Vaya a **Pago y administración de mi riesgo** > **Bloquear pagos** y haga clic en **Actualizar**.
1. **Preferencias de venta**, haz clic en **Preferencias de recepción de pago**.
1. En **Bloquear pagos accidentales**, elija **No, permitir varios pagos por identificador de factura**.    ![paypal_allow_multiple_payments_per_invoice_id.png](assets/paypal_allow_multiple_payments_per_invoice_id.png)
1. Desplácese hacia abajo y haga clic en **Guardar**.

## Más información

* [Bloquear pagos accidentales](https://developer.paypal.com/docs/admin/setup-account/#block-accidental-payments) en los documentos para desarrolladores de PayPal.
* Pagos mediante PayPal en nuestra guía de usuario:
   * [Pago y envío con PayPal Express](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html)
   * [Otras soluciones de PayPal](/docs/commerce-admin/stores-sales/payments/paypal/paypal.html)
* En nuestra documentación para desarrolladores:
   * [Configurar métodos de pago de PayPal para Adobe Commerce en la infraestructura en la nube](/docs/commerce-cloud-service/user-guide/configure-store/paypal.html)
   * [Integraciones de pagos](https://developer.adobe.com/commerce/php/development/payments-integrations/)
