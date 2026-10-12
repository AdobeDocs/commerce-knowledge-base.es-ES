---
title: 'Adobe Commerce 2.4.1: mensaje incorrecto en el cierre de compra de PayPal-Braintree para invitados'
description: Este artículo describe un problema conocido de Adobe Commerce 2.4.1 en el que, si el cierre de compra de un invitado está deshabilitado, un cliente invitado que intenta realizar un pedido con PayPal a través de Braintree recibe un mensaje de error no informativo.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
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
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%
---
# Adobe Commerce 2.4.1: mensaje incorrecto en el cierre de compra de PayPal-Braintree para invitados

Este artículo describe un problema conocido de Adobe Commerce 2.4.1 en el que, si el cierre de compra de un invitado está deshabilitado, un cliente invitado que intenta realizar un pedido con PayPal a través de Braintree recibe un mensaje de error no informativo.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0, 2.4.1
* Adobe Commerce en infraestructura en la nube 2.4.0, 2.4.1

## Problema

Se muestra un error inespecífico cuando el pago de los invitados está desactivado desde el backend y la opción de pago PayPal a través de Braintree está seleccionada en el minicarrito o el carro de compras.

<u>Requisitos previos</u>:

1. En el Administrador de Commerce, en **Tiendas** > **Configuración** > **Ventas** > **Cierre de compra**, establezca **Permitir cierre de compra de invitados** = *No*.
1. Habilite PayPal a través de Braintree como se describe en [Braintree] (¿https://experienceleague.adobe.com/es/docs/commerce-admin/stores-sales/payments/braintree?) en nuestra guía del usuario.

<u>Pasos a seguir</u>:

1. Añadir un producto al carro de compras como invitado.
1. Selecciona **Minicarrito** y haz clic en **Pagar con PayPal**.
1. Completa el proceso de pago por PayPal y luego llegarás a la página de revisión de pedidos.
1. Seleccione **Método de envío**.
1. Haga clic en **Realizar pedido**.

<u>Resultados esperados</u>:

Cuando un cliente hace clic en el botón PayPal de la página del minicarrito o del carro de compras, se le debe mostrar el siguiente mensaje:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Si habilitas PayPal directo sin usar Braintree, este escenario se comporta de forma diferente. No permite al usuario invitado continuar con el proceso de pago. Mostrará el siguiente mensaje cuando el usuario invitado haga clic en el botón PayPal en el minicarrito:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>Resultados reales</u>:

Se redirige al cliente a la página Carro de compras y se muestra el siguiente mensaje:

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Solución

La solución a este problema es que el cliente puede iniciar sesión en una tienda (los usuarios que iniciaron sesión no usan el pago de invitados). donde la comprobación de invitado está deshabilitada. Este problema se solucionó en la versión 2.4.2 de Adobe Commerce.

## Lectura relacionada

* [Práctica recomendada para la cantidad de productos que hay en el carro de compras en Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) en nuestra base de conocimiento de soporte.
* [Tutorial de procesamiento de pedidos: Paso 1. Agregue elementos al carro de compras &#x200B;](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/) en nuestra documentación para desarrolladores
* [Tutorial de cierre de compra de GraphQL: Paso 1. Agregue productos al carro &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) en nuestra documentación para desarrolladores
