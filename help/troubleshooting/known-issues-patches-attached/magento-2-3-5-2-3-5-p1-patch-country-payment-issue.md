---
title: "parche de Adobe Commerce 2.3.5, 2.3.5-p1: problema con el pago por país"
description: Este parche resuelve un problema en Adobe Commerce en el que el flujo de trabajo de cierre de compra de la tienda no mostraba ningún método de pago que se hubiera habilitado para países específicos, excepto Klarna y Amazon Pay.
exl-id: e205e35e-9ffe-4826-b951-3a3caf1e0621
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# parche de Adobe Commerce 2.3.5, 2.3.5-p1: problema de pago por país

Este parche resuelve un problema en Adobe Commerce en el que el flujo de trabajo de cierre de compra de la tienda no mostraba ningún método de pago que se hubiera habilitado para países específicos, excepto Klarna y Amazon Pay.

## Productos y versiones afectados

* Adobe Commerce en la nube 2.3.5 y 2.3.5-p1
* Adobe Commerce local 2.3.5 y 2.3.5-p1

## Problema

Cuando una tienda tiene Amazon Pay y otro pago asignado a diferentes países, y cuando se selecciona uno de esos países y métodos de pago, los botones de forma de pago y realizar pedido no están visibles.

Una actualización de página web es una solución para el problema.

Para resolver este problema y eliminar el error, hemos creado un [parche](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip).

<u>Requisitos previos</u>:

* Se crea un producto simple.
* El cheque o giro postal **1} solo está habilitado en determinados países (en** Tienda **>** Configuración **>** Ventas **>** Métodos de pago **).**

* Ejemplo: Pago de Países Aplicables = Países Específicos
* Ejemplo: Pago desde países específicos = Reino Unido

<u>Pasos a seguir</u>:

1. Vaya a la Tienda como invitado.
1. Agregue un producto simple al carro de compras.
1. Vaya a Cierre de compra.
1. Rellene el formulario con datos válidos.

   * País = *Estados Unidos*

1. Seleccione la tarifa de envío y haga clic en **Siguiente**.

   * Se abre el paso de pago.
   * No hay pagos disponibles.
   * Mensaje: **No hay ninguna forma de pago disponible.**
   * No hay ningún botón **Realizar pedido**.

1. Vuelva al **Paso de envío** y cambie el valor a:

   * País = *Reino Unido*

1. Seleccione la tarifa de envío y haga clic en **Siguiente**.

<u>Resultado esperado</u>:

Se abre el paso Pago.

* **Pago contra reembolso** aparece.
* Aparece **Cheque/giro postal**.
* Aparece el botón **Realizar pedido**.

<u>Resultado real</u>:

Se abre el paso Pago.

* No hay pagos disponibles.
* Mensaje: *No hay ninguna forma de pago disponible.*
* No hay ningún botón **Realizar pedido**.

## Solución

[Aplicar el parche](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) siguiente.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar BUNDLE-2546\_EE\_2.3.5-p1.composer.patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la nube 2.3.5 y 2.3.5-p1
* Adobe Commerce local 2.3.5 y 2.3.5-p1

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce versiones 2.3.4-p2 - 2.2.6

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Archivos adjuntos
