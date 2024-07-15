---
title: "Problema de Adobe Commerce 2.4.0: visualización de datos de mensaje sin procesar de tienda"
description: Este artículo proporciona una solución para el problema cuando todos los mensajes de error en la tienda se muestran con un signo "+" en lugar de un espacio. Esta solución ayuda a que los mensajes de error sean legibles.
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Problema de Adobe Commerce 2.4.0: visualización de datos de mensajes sin procesar de tienda

Este artículo proporciona una solución para el problema cuando todos los mensajes de error en la tienda se muestran con un signo &quot;+&quot; en lugar de un espacio. Esta solución ayuda a que los mensajes de error sean legibles.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.0
* Adobe Commerce local 2.4.0.

## Problema

<u>Pasos a seguir:</u>

1. Vaya a la página **Crear nueva cuenta** de la tienda.
1. Cree una nueva cuenta mediante un correo electrónico registrado. Se muestra el siguiente mensaje:

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## Causa

El problema se debe a un problema de PHP 7.4.2 relacionado con las cookies set\\read. Consulte [PHP BUG \#79174 setcookie() codifica el espacio como \`+\`, pero $\_COOKIE ya no los descodifica](https://bugs.php.net/bug.php?id=79174).

## Solución

Para resolver este problema, use otra versión de PHP 7.4.x. Adobe Commerce 2.4.0 no admite PHP 7.4.2.

## Lecturas relacionadas en nuestra base de conocimiento de soporte:

* [Problema conocido de Commerce 2.4.0: los métodos de pago del Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de creación de etiquetas de envío en Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema conocido de Adobe Commerce 2.4.0: la actualización de las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: Exportar tipos impositivos no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Añadir selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
