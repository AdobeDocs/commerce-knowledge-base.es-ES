---
title: Parche para el problema de cierre de compra de Amazon Pay en Adobe Commerce 2.3.5-p1
description: Este parche resuelve el problema de la incapacidad para cambiar un método de pago en el paso "Revisión y pagos" de pago desde el widget de pagos, mientras se realiza el pago con Amazon Pay en Adobe Commerce.
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Parche para el problema de cierre de compra de Amazon Pay en Adobe Commerce 2.3.5-p1

Este parche resuelve el problema de la incapacidad para cambiar un método de pago en el paso &quot;Revisión y pagos&quot; de pago desde el widget de pagos, mientras se realiza el pago con Amazon Pay en Adobe Commerce.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube versión 2.3.5-p1
* Adobe Commerce local versión 2.3.5-p1

## Problema

Cuando un comprador cierra la compra con Amazon Pay, inicia sesión, continúa con el paso de pago e intenta cambiar su tarjeta de crédito de pago desde el widget de pagos, aparece un mensaje de error. El cierre de compra no se puede completar si el comprador ignora el error y continúa con el cierre de compra.

Para resolver este problema y eliminar el error, se ha creado un [parche](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip).

<u>Pasos a seguir</u>:

1. Inicia el proceso de pago y envío con Amazon Pay.
1. Inicie sesión como cliente de Amazon Pay.
1. Seleccione el método de envío y continúe con el paso de pago.
1. Intente cambiar la tarjeta de crédito por otra diferente.

<u>Resultado esperado</u>: Se selecciona una tarjeta de crédito diferente como método de pago sin error.

<u>Resultado real</u>: Aparece el mensaje de error: *&quot;Póngase en contacto con este comerciante para que le ayude a completar su pedido&quot;.*

## Solución

[Aplicar el parche](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) más abajo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar BUNDLE-2554\_EE\_2.3.5-p1.composer.patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube versión 2.3.5-p1
* Adobe Commerce local versión 2.3.5-p1

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en la infraestructura en la nube versión 2.3.5
* Adobe Commerce local versión 2.3.5

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Archivos adjuntos
