---
title: "Adobe Commerce 2.4.0, 2.4.1: Habilitar factura parcial Venmo de Braintree"
description: En este artículo se describe una emisión conocida de Adobe Commerce 2.4.0 y 2.4.1 en la que la factura parcial no está disponible para pedidos realizados con Braintree a través de Venmo.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0, 2.4.1: Habilitar factura parcial Venmo de Braintree

En este artículo se describe una emisión conocida de Adobe Commerce 2.4.0 y 2.4.1 en la que la factura parcial no está disponible para pedidos realizados con Braintree a través de Venmo.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0 y 2.4.1
* Adobe Commerce en la infraestructura en la nube 2.4.0 y 2.4.1

## Problema

<u>Requisitos previos:</u>

En la configuración del método de pago del Braintree, establezca **Habilitar Venmo a través del Braintree** = *Sí* con **Acción de pago** = *Autorización*; **Habilitar Vault para pagos con tarjeta** = *No*.

<u>Pasos a seguir:</u>

1. Cree un pedido de dos o más productos con Venmo (Braintree) como forma de pago.
1. Abra el pedido en el Administrador de Commerce.
1. Cree una factura para uno de los productos pedidos.
1. Intente crear una factura para el resto de los productos pedidos.

<u>Resultado esperado:</u>

Factura creada.

<u>Resultado real:</u>

Se muestra el siguiente mensaje de error: *El comando &quot;vault\_capture&quot; no existe. Compruebe el comando e inténtelo de nuevo.*

## Solución

Registra el importe total al crear facturas para pedidos realizados con Braintree a través de Venmo.
