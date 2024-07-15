---
title: "Problema conocido de Adobe Commerce 2.3.7-p1: total de pedido obsoleto para PayPal"
description: '"Este artículo proporciona un parche para un problema conocido en Adobe Commerce 2.3.7-p1: cuando se utiliza el cierre de compra de PayPal más de una vez, los clientes obtienen el producto solicitado anteriormente en el carro, en lugar del nuevo que están intentando solicitar".'
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.3.7-p1: total de pedido obsoleto para PayPal

Este artículo proporciona un parche para un problema conocido de Adobe Commerce 2.3.7-p1: cuando se utiliza el cierre de compra de PayPal más de una vez, los clientes obtienen el producto solicitado anteriormente en el carro de compras, en lugar del nuevo que están intentando solicitar.
Puede descargar el parche desde este artículo y también está disponible a través de la herramienta Parches de calidad (QPT).

## Versiones afectadas

* Adobe Commerce (todas las opciones de implementación) 2.3.7-p1
* Magento Open Source 2.3.7-p1

## Problema

Al realizar un pedido mediante el método de pago PayPal Express Checkout, el producto comprado previamente pedido se añade al pedido en lugar del real.

<u>Pasos a seguir:</u>

1. En el frente de la tienda, añada cualquier producto al carro de compras (producto A, precio $50).
1. Haga clic en el vínculo carro de compras para abrirlo.
1. Haz clic en el botón **Pago y envío por PayPal**.
1. Utiliza tus credenciales de PayPal para iniciar sesión en PayPal y enviar el pago.
1. Finalizar la colocación del pedido en la tienda.
1. Vuelva al catálogo y añada un producto diferente (producto B, precio 100 $) al carro de compras.
1. Haga clic en el vínculo carro de compras para abrirlo.
1. Haz clic en el botón **Pago y envío por PayPal**.

<u>Resultado real:</u>

El precio del producto en el carro es de 50 $ en lugar de 100 $.<br/>
En el lado de la tienda, el pedido contiene el producto A en lugar del producto B.

<u>Resultado esperado:</u>

El producto B se añade al pedido.

## Solución

Aplique el parche proporcionado en este artículo.

## Parche

Use el siguiente vínculo para descargar un archivo .zip que contenga el parche: [MC42674-composer.patch.zip](assets/MC42674-composer.patch.zip).

### Versiones de Adobe Commerce compatibles

* Adobe Commerce (todas las opciones de implementación) 2.3.7-p1

## Cómo aplicar los parches

1. Descomprima el archivo .zip descargado.
1. Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener más instrucciones.
