---
title: "Adobe Commerce 2.4.4: No se pueden crear facturas parciales"
description: Este artículo proporciona una revisión para el problema en el que los usuarios no pueden crear facturas parciales al utilizar Apple Pay o Google Pay mediante Braintree como métodos de pago.
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4: No se pueden crear facturas parciales

Este artículo proporciona una revisión para el problema en el que los usuarios no pueden crear facturas parciales al utilizar Apple Pay o Google Pay mediante Braintree como métodos de pago.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.4.4

## Problema

Al usar Apple Pay o Google Pay como métodos de pago, los usuarios reciben el error &quot;*El comando ‘vault_capture’ no existe. Compruebe el comando e inténtelo de nuevo.*&quot; al crear facturas parciales.

<u>Pasos a seguir</u>:

1. Abra el sitio web de Adobe Commerce.
1. Añadir un producto simple al carro de compras (cantidad 2).
1. Elige **Apple Pay** o **Google Pay** como forma de pago del carro de compras.
1. Realice el pedido.
1. Abra los detalles del pedido desde el back-end.
1. Crear una factura parcial.
1. Crear otra factura para el importe restante.

<u>Resultados esperados</u>:

Se crean facturas parciales.

<u>Resultados reales</u>:

Se crea la primera factura parcial. Al crear la segunda factura parcial, los usuarios reciben el siguiente error: *El comando ‘vault_capture’ no existe. Compruebe el comando e inténtelo de nuevo*.

## Causa

Adobe Commerce guarda los detalles de la tarjeta de crédito en el almacén para crear facturas parciales. Actualmente, no hay ninguna funcionalidad para proteger Apple Pay y Google Pay.

## Solución

Para resolver el problema, aplique el siguiente parche:

[Braintree_disabled_partial_capture_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.
