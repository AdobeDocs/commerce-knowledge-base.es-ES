---
title: 'Adobe Commerce 2.4.1: mensaje incorrecto en el cierre de compra de PayPal-Braintree'
description: Este artículo describe un problema conocido de Adobe Commerce 2.4.1 en el que, si el cierre de compra de un invitado está deshabilitado, un cliente invitado que intenta realizar un pedido con PayPal a través de Braintree recibe un mensaje de error no informativo.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: mensaje incorrecto en el cierre de compra de PayPal-Braintree

Este artículo describe un problema conocido de Adobe Commerce 2.4.1 en el que, si el cierre de compra de un invitado está deshabilitado, un cliente invitado que intenta realizar un pedido con PayPal a través de Braintree recibe un mensaje de error no informativo.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0, 2.4.1
* Adobe Commerce en infraestructura en la nube 2.4.0, 2.4.1

## Problema

Se muestra un error inespecífico cuando el pago de los invitados está desactivado desde el backend y la opción de pago mediante Braintree de PayPal está seleccionada en el minicarrito o en el carro de compras.

<u>Requisitos previos</u>:

1. En el Administrador de Commerce, en **Tiendas** > **Configuración** > **Ventas** > **Cierre de compra**, establezca **Permitir cierre de compra de invitados** = *No*.
1. Habilite PayPal a través del Braintree como se describe en [Braintree](https://experienceleague.adobe.com/es/docs/commerce-admin/stores-sales/payments/braintree?) en nuestra guía de usuario.

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

La solución a este problema es que el cliente puede iniciar sesión en una tienda (los usuarios que iniciaron sesión no usan el cierre de compra de invitados) en la que el cierre de compra de invitados esté deshabilitado. Este problema se solucionó en la versión 2.4.2 de Adobe Commerce.

## Lectura relacionada

* [Práctica recomendada para la cantidad de productos que hay en el carro de compras en Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) en nuestra base de conocimiento de soporte.
* [Tutorial de procesamiento de pedidos: Paso 1. Agregue elementos al carro de compras &#x200B;](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/) en nuestra documentación para desarrolladores
* [Tutorial de cierre de compra de GraphQL: Paso 1. Agregue productos al carro &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) en nuestra documentación para desarrolladores
