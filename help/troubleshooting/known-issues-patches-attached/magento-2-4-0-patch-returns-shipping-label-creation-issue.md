---
title: "parche de Adobe Commerce 2.4.0: devuelve el problema de creación de la etiqueta de envío"
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.4.0 cuando hay un problema con la impresión de una etiqueta de envío para las devoluciones de los clientes.
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# parche de Adobe Commerce 2.4.0: devuelve el problema de creación de etiquetas de envío

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.4.0 cuando hay un problema con la impresión de una etiqueta de envío para las devoluciones de los clientes.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.0
* Adobe Commerce local 2.4.0

## Problema

<u>Pasos a seguir:</u>

1. Realice y complete un pedido con uno de los siguientes métodos de envío principales: FedEx, DHL, UPS y USPS.
1. Cree y autorice devoluciones para este pedido.
1. Abra una página **Información de devolución** autorizada y haga clic en el botón **Crear etiqueta de envío**.
1. Seleccione el método de envío, añada un producto a un paquete y haga clic en Guardar.

<u>Resultado esperado:</u>

Se ha creado correctamente una etiqueta de envío y verá un mensaje: *Ha creado una etiqueta de envío.*

<u>Resultado real:</u>

La página **Devolver información** está dañada y verá un mensaje de error en la página Devolver información: *Se han realizado cambios de información general en esta sección que no se han guardado. Esta ficha contiene datos no válidos*.

## Solución

Aplicar [parche](assets/MC-35984-2.4.0-CE-composer.patch.zip) proporcionado en este artículo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[MC-35984-2.4.0-CE-composer.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

El parche también está disponible para su descarga en los formatos `.git` y `.composer` de la página [Descargas de Adobe Commerce](https://magento.com/tech-resources/download), en **Parches** en la navegación de la columna izquierda. Busque el parche de MC-35984.

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra página de conocimientos de soporte técnico.

## Lecturas relacionadas en nuestra base de conocimiento de soporte:

* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensaje sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: Exportar tipos impositivos no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago del Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema conocido de Adobe Commerce 2.4.0: error de visualización de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
