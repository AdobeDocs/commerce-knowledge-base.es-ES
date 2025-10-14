---
title: 2.3.4 Revisión de problemas de PayPal
description: Este artículo proporciona una corrección de los errores recibidos durante la realización del pedido al seleccionar una región en Pago y envío con PayPal Express. El problema se debe a los cambios realizados en la versión 2.3.4 de Adobe Commerce y está relacionado con el modo en que se analizan los campos de dirección de Pago y envío de PayPal Express.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 Revisión de problemas de PayPal

Este artículo proporciona una corrección de los errores recibidos durante la realización del pedido al seleccionar una región en Pago y envío con PayPal Express. El problema se debe a los cambios realizados en la versión 2.3.4 de Adobe Commerce y está relacionado con el modo en que se analizan los campos de dirección de Pago y envío de PayPal Express.

## Versiones y productos afectados

* Adobe Commerce en infraestructura en la nube v2.3.4
* Adobe Commerce local v2.3.4

## Problema

Se produce un error al introducir el país y la región durante la realización del pedido en PayPal Express Checkout. El problema se puede reproducir en cualquier país donde el campo de región de la sección de dirección sea un campo de texto (en lugar de un menú desplegable).

<u>Pasos a seguir</u> :

1. Activar Pago y envío de PayPal Express.
1. Añadir un producto al carro de compras como invitado o cuando haya iniciado sesión.
1. Vaya a Pago y envío.
1. Selecciona tu dirección de envío. Por ejemplo, *UK*. A continuación, introduzca una entrada en el campo **Estado/Provincia**. Por ejemplo, *Nottinghamshire*.
1. Haga clic en el botón **Realizar pedido** para realizar el pedido. Recibe una página de pedido correcta y un correo electrónico de confirmación de pedido.

<u>Resultado esperado:</u>

El pedido se ha realizado correctamente.

<u>Resultado real:</u>

Cuando se hace clic en el botón Ordenar, se muestra un error:

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Solución

Para comerciantes locales de Adobe Commerce: aplique la revisión [hotfix,](https://magento.com/tech-resources/download#download2353) que está disponible en la sección Descargas del portal [magento.com](https://magento.com) en Mi cuenta.

Para Adobe Commerce en comerciantes de infraestructura en la nube: Adobe ha incluido la corrección en los parches de nube para Commerce v1.0.2. Consulte [Parches de nube para las notas de la versión de Commerce](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches?itm_source=devdocs&itm_medium=quick_search&itm_campaign=federated_search&itm_term=cloud%20patche) en nuestra documentación para desarrolladores para obtener instrucciones sobre cómo aplicar el paquete más reciente.

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Lectura relacionada

* [Información de la versión > Notas de la versión de Adobe Commerce 2.3.4 > Aplique el problema de cierre de compra de PayPal Express con el parche de región para Adobe Commerce 2.3.4 para solucionar un problema crítico de cierre de compra de PayPal Express](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) en nuestra documentación para desarrolladores.
