---
title: "Adobe Commerce 2.3.6: el control de número ilimitado se muestra al guardar la dirección"
description: En este artículo se describe un problema conocido de Adobe Commerce 2.3.6 en el que el indicador de número en espera se muestra indefinidamente al guardar una dirección en Mi cuenta en la tienda.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Adobe Commerce 2.3.6: control de número ilimitado mostrado al guardar la dirección

En este artículo se describe un problema conocido de Adobe Commerce 2.3.6 en el que el indicador de número en espera se muestra indefinidamente al guardar una dirección en Mi cuenta en la tienda.

## Productos y versiones afectados

* Adobe Commerce 2.3.6 con la integración de Vertex habilitada (solo para el navegador Firefox)

## Problema

Al guardar una dirección en la sección Mi cuenta de la tienda, a veces el control de número de espera se muestra indefinidamente debido a un error en el JS principal de Vértice.

## Solución

Solución alternativa: use un explorador alternativo para Firefox.

El problema se solucionó en Adobe Commerce 2.3.1.

## Lectura relacionada

* [No se permiten direcciones diferentes al anular la selección de &quot;Mi dirección de facturación y de envío es la misma&quot; mediante la limpieza de direcciones de vértice](/help/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.md) en nuestra base de conocimiento de soporte.
* [Mensaje de validación de dirección de vértice de Adobe Commerce 2.4.1: Actualización de dirección de publicación](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) en nuestra base de conocimiento de soporte.
