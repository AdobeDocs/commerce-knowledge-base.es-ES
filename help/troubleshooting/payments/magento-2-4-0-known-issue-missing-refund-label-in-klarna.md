---
title: 'Problema conocido de Adobe Commerce 2.4.0: falta la etiqueta "Reembolso" en Klarna'
description: Este artículo proporciona una solución para un problema conocido en Administración para una etiqueta **Reembolso** que falta en Klarna VBE (extensión agrupada de proveedor). Cuando en el portal de Klarna se realiza un reembolso, la etiqueta **Reembolso** no se muestra junto al producto agrupado que se reembolsó.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%
---
# Problema conocido de Adobe Commerce 2.4.0: falta la etiqueta &quot;Reembolso&quot; en Klarna

Este artículo proporciona una solución para un problema conocido en Administración para una etiqueta **Reembolso** que falta en Klarna VBE (extensión agrupada de proveedor). En el portal de Klarna que realiza un reembolso, la etiqueta **Reembolso** no se muestra junto al producto agrupado que se reembolsó.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Requisitos previos:</u>

* Klarna está habilitado.
* Se crea un producto agrupado.

<u>Pasos a seguir</u>

1. Vaya al front-end de Adobe Commerce y agregue un producto agrupado al **carro**.
1. Vaya a Cierre de compra.
1. Escriba la información del consumidor en el cierre de compra y haga clic en **Siguiente**.
1. Seleccione **KP option** y haga clic en **Realizar pedido**.
1. Vaya a **Administración** > **Ventas** > **Pedidos**.
1. Abra el pedido.
1. Crear factura para el producto.
1. Vaya a **Facturas** > **Seleccionar factura** > Haga clic en **Nota de crédito** > Haga clic en **Reembolso** (no en **Reembolso sin conexión**).
1. Ve al portal Klarna.
1. Abra el pedido.
1. La etiqueta **Reembolso** está presente.

<u>Resultado esperado</u>

En el portal de Klarna, la etiqueta **Reembolso** se muestra junto al producto que se reembolsó.

<u>Resultado real</u>

En el portal de Klarna, la etiqueta **Reembolso** no se muestra al lado del producto que ha sido reembolsado.

## Solución

La solución a este problema es ignorar la etiqueta **Reembolso** que falta en el portal de Klarna para los productos agrupados con reembolso. Se ha realizado el reembolso, aunque no se mostraba la etiqueta **Reembolso**. Se espera que el problema se solucione en Adobe Commerce 2.4.1, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lecturas relacionadas en nuestra base de conocimiento de soporte:

* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
