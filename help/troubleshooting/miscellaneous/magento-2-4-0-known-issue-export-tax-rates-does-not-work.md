---
title: 'Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan'
description: Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 en el que el botón **Exportar tipos impositivos** no funciona.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan

Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 donde el botón **Exportar tasas de impuestos** no funciona.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.0
* Adobe Commerce local 2.4.0

## Problema

<u>Pasos a seguir:</u>

1. Vaya al Panel de administración de Commerce > **Tiendas** > **Reglas fiscales**.
1. Haga clic en el botón **Agregar nueva regla fiscal**.
1. Haga clic en el texto del botón **Exportar tipos impositivos**.

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Resultado esperado</u>:

Un archivo `tax_rates.csv` descarga las tasas de impuestos que contiene.

<u>Resultado real</u>:

No se ha descargado ningún archivo .csv.

## Solución

Solución alternativa:

Haga clic en el borde inferior izquierdo del botón **Exportar tipos impositivos** para exportar el archivo `tax_rates.csv`.

![magento_export_tax_rates.png](assets/mceclip1.png)

Se prevé que el problema se resuelva en un parche de la versión 2.4.1.

## Lectura relacionada

En nuestra base de conocimiento de soporte:

* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago del Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Problema conocido de creación de etiquetas de envío en Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md).
* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Problema conocido de Adobe Commerce 2.4.0: se muestran datos de mensajes sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [Problema conocido de Adobe Commerce 2.4.0: El botón &quot;Agregar selecciones a mi carro de compras&quot; no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
