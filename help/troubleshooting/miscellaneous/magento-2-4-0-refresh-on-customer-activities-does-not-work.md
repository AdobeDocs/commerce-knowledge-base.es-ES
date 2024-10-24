---
title: "Adobe Commerce 2.4.0: la actualización de las actividades del cliente no funciona"
description: Este artículo proporciona una solución para el problema conocido de Adobe Commerce 2.4.0 cuando un usuario administrador crea un pedido para un cliente y los botones de actualización del panel lateral Actividades del cliente no funcionan.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: la actualización de las actividades del cliente no funciona

Este artículo proporciona una solución para el problema conocido de Adobe Commerce 2.4.0 cuando un usuario administrador crea un pedido para un cliente y los botones de actualización del panel lateral Actividades del cliente no funcionan.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Pasos a seguir</u>:

1. Vaya a **Panel de administración** > **Ventas** > **Pedidos**.
1. Haga clic en el botón **Crear nuevo pedido**.
1. Seleccione el cliente creado.
1. Vaya a la tienda como cliente creado.
1. Vaya a la página **Producto**. Haga clic en el botón **Actualizar** en la sección **Productos vistos recientemente** de **Actividades del cliente**.
1. Vuelve a la tienda.
1. Realice un pedido utilizando los productos creados.
1. Vuelva al **Panel de administración** y haga clic en el botón **Actualizar** de la sección **Últimos artículos pedidos** de **Actividades del cliente**.
1. Vuelve a la tienda. Agregue el producto creado a la **Lista de comparación**.
1. Volver al **Panel de administración**. Haga clic en el botón **Actualizar** de la sección **Productos en la lista de comparación** de **Actividades del cliente**.
1. Vuelve a la tienda.
1. Quitar el producto creado de la **Lista de comparación**.
1. Volver al **Panel de administración**.
1. Haga clic en el botón **Actualizar** de la sección **Productos comparados recientemente** de **Actividades del cliente**.
1. Vuelve a la tienda.

<u>Resultados esperados</u>:

El nombre del producto debe aparecer en las secciones **Productos vistos recientemente**, **Últimos artículos pedidos**, **Productos en la lista de comparación** y **Productos comparados recientemente**.

<u>Resultados reales</u>:

La página se desplaza hacia arriba cada vez que se hace clic en un botón **Actualizar**. El nombre del producto no aparece en la sección adecuada.

## Solución

Una solución es que el usuario administrador puede actualizar **las actividades del cliente** haciendo clic en el botón **Actualizar cambios** en la parte inferior de la barra lateral. Está previsto resolver el problema en el parche de Adobe Commerce 2.4.1.

![mceclip0.png](assets/mceclip0.png)

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago del Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensaje sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: Exportar tipos impositivos no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
