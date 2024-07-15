---
title: Los clientes de la UE no pueden completar pagos
description: Este artículo soluciona el problema de que los clientes de la Unión Europea no puedan completar los pagos.
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Los clientes de la UE no pueden completar pagos

Este artículo soluciona el problema de que los clientes de la Unión Europea no puedan completar los pagos.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones
* Adobe Commerce local 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problema

Los clientes de la UE se quejan de que sus transacciones con tarjetas de crédito están siendo rechazadas.

## Causa

La Unión Europea revisó una regulación llamada Directiva de servicios de pago (PSD) con una versión actualizada [PSD 2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN). Se trata de una directiva de la Unión Europea (UE) que regula los servicios de pago y los proveedores de servicios de pago en toda la UE y en el Espacio Económico Europeo (EEE). La autenticación de cliente sólida (SCA) es un requisito de PSD2 para aumentar la seguridad y autenticación de los datos de pago. Si sus soluciones de pago no cumplen con los requisitos de la directiva, esto puede resultar en que los clientes no puedan completar los pagos. Encuentre más detalles en la [publicación relacionada del DevBlog de Adobe Commerce](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460).

## Solución

Siga las recomendaciones de la sección [Adobe Commerce Payment Provider Recommendations del DevBlog](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations).
