---
title: Adobe Commerce solicita a los clientes que inicien sesión en un vínculo no válido
description: El artículo proporciona un vínculo al parche para un problema conocido de Adobe Commerce 2.3.5, en el que se solicita a los clientes que inicien sesión, pero el vínculo para reenviar un correo electrónico de confirmación no funciona.
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce solicita a los clientes que inicien sesión en un vínculo no válido

El artículo proporciona un vínculo al parche para un problema conocido de Adobe Commerce 2.3.5, en el que se solicita a los clientes que inicien sesión, pero el vínculo para reenviar un correo electrónico de confirmación no funciona.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.3.5

## Problema

Adobe Commerce solicita a los clientes que inicien sesión mostrando este mensaje: *&quot;Esta cuenta no está confirmada. Haga clic aquí para reenviar el correo electrónico de confirmación&quot;*. El **Haga clic aquí** El vínculo debe abrir la página Enviar vínculo de confirmación, pero está inactivo.

## Solución

Hay un parche para este problema disponible en Recursos técnicos de Adobe Commerce: [Reenviar parche de problema de vínculo de correo electrónico de confirmación de cuenta para Adobe Commerce 2.3.5](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368). Habrá disponible una corrección permanente en Adobe Commerce 2.3.6, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones sobre cómo aplicar un parche de composer.

## Lectura relacionada

Artículos de nuestra base de conocimiento de soporte y documentación para desarrolladores para problemas conocidos de Adobe Commerce 2.3.5:

* [Problema conocido de Adobe Commerce 2.3.5: pedidos de varios envíos de productos virtuales](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Problema conocido en Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [parche de Adobe Commerce 2.3.5, 2.3.5-p1: problema de pago por país](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce solicita a los clientes que inicien sesión en un vínculo no válido](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Problema conocido del recuento de productos de acción masiva en Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Parche para el problema de cierre de compra de Amazon Pay en Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Problemas conocidos de Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
