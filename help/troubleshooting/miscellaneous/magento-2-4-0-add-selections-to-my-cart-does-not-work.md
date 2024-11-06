---
title: '"Adobe Commerce 2.4.0: "Añadir selecciones a mi carro de compras" no funciona"'
description: Este artículo proporciona una solución para un problema conocido relacionado con un botón roto en el administrador de Commerce al administrar el carro de compras de un cliente. Al intentar agregar los productos seleccionados al carro de compras de un cliente, el botón **Agregar selecciones al carro de compras** situado en la parte inferior de la sección no funciona. Este problema se produce en cualquier página del panel de administración que contenga dos botones **Agregar selecciones al carro de compras**. Habrá disponible una corrección permanente en Adobe Commerce 2.4.1.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: &quot;Añadir selecciones a mi carro de compras&quot; no funciona

Este artículo proporciona una solución para un problema conocido relacionado con un botón roto en el administrador de Commerce al administrar el carro de compras de un cliente. Al intentar agregar los productos seleccionados al carro de compras de un cliente, el botón **Agregar selecciones a mi carro** ubicado en la parte inferior de la sección no funciona. Este problema ocurre en cualquier página del panel de administración que contenga dos botones **Agregar selecciones a mi carro de compras**. Habrá disponible una corrección permanente en Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce 2.4.0 (todos los métodos de implementación)

## Problema

<u>Pasos a seguir</u>

1. Vaya a cualquier página del panel de administración que contenga dos botones **Agregar selecciones a mi carro de compras**.
1. Seleccionar elementos para agregar a mi carro de compras.
1. Haga clic en el botón **Agregar selecciones a mi carro** ubicado en la parte inferior de la sección.

<u>Resultado esperado</u>

Todas las selecciones se añaden al carro de compras según lo esperado.

<u>Resultado real</u>

Adobe Commerce no agrega sus selecciones al carro de compras.

## Solución

El botón **Agregar selecciones a mi carro** ubicado en la parte superior de la página sigue funcionando. Se espera que el problema se solucione en la versión 2.4.1 de Adobe Commerce, cuyo lanzamiento está programado para el cuarto trimestre de 2011.

## Lectura relacionada

* Administración de un carro de compras por parte de [MerchDocs](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage) en nuestra guía del usuario.
* [Problema conocido de Adobe Commerce 2.4.0: los datos de mensajes sin procesar se muestran en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md) de nuestra base de conocimiento de soporte.
* [Problema conocido de Adobe Commerce 2.4.0: las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) en nuestra base de conocimiento de soporte.
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago del Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) en nuestra base de conocimiento de soporte técnico.
