---
title: "Adobe Commerce 2.4.0: la actualización de las actividades del cliente no funciona"
description: Este artículo proporciona una solución para el problema conocido de Adobe Commerce 2.4.0 cuando un usuario administrador crea un pedido para un cliente y los botones de actualización del panel lateral Actividades del cliente no funcionan.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: la actualización de las actividades del cliente no funciona

Este artículo proporciona una solución para el problema conocido de Adobe Commerce 2.4.0 cuando un usuario administrador crea un pedido para un cliente y los botones de actualización del panel lateral Actividades del cliente no funcionan.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Pasos a seguir</u>:

1. Vaya a la **Panel de administración** > **Ventas** > **Pedidos**.
1. Haga clic en **Crear nuevo pedido** botón.
1. Seleccione el cliente creado.
1. Vaya a la tienda como cliente creado.
1. Vaya a la **Product** página. Haga clic en **Actualizar** botón en el **Productos vistos recientemente** sección de **Actividades del cliente**.
1. Vuelve a la tienda.
1. Realice un pedido utilizando los productos creados.
1. Vuelva a la **Panel de administración** y haga clic en **Actualizar** del botón **Últimos artículos pedidos** sección de **Actividades del cliente**.
1. Vuelve a la tienda. Añadir el producto creado a **Lista de comparación**.
1. Vuelva a la **Panel de administración**. Haga clic en **Actualizar** del botón **Productos en la lista de comparación** sección de **Actividades del cliente**.
1. Vuelve a la tienda.
1. Elimine el producto creado de **Lista de comparación**.
1. Vuelva a la **Panel de administración**.
1. Haga clic en **Actualizar** del botón **Productos comparados recientemente** sección de **Actividades del cliente**.
1. Vuelve a la tienda.

<u>Resultados esperados</u>:

El nombre del producto debe aparecer en la **Productos vistos recientemente**, **Últimos artículos pedidos**, **Productos en la lista de comparación**, y **Productos comparados recientemente** sección.

<u>Resultados reales</u>:

La página se desplaza hacia arriba cada vez que **Actualizar** Haga clic en el botón. El nombre del producto no aparece en la sección adecuada.

## Solución

El usuario administrador puede actualizar una solución **Actividades del cliente** haciendo clic en **Actualizar cambios** en la parte inferior de la barra lateral. Está previsto resolver el problema en el parche de Adobe Commerce 2.4.1.

![mceclip0.png](assets/mceclip0.png)

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago del Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de creación de etiquetas de envío en Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensaje sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: Exportar tipos impositivos no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
