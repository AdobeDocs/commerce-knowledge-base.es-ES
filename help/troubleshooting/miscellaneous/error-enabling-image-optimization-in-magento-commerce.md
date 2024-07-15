---
title: Error al habilitar la optimización de imágenes en Adobe Commerce
description: Este artículo proporciona una solución para el problema cuando la optimización de imágenes (IO) rápida está deshabilitada de forma predeterminada con una notificación para ponerse en contacto con Fastly para habilitar la optimización de imágenes. (Fastly Cloud Image Optimizer es un servicio de optimización y manipulación de imágenes en tiempo real que acelera la entrega de imágenes al ofrecer imágenes con un ancho de banda eficiente).
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Error al habilitar la optimización de imágenes en Adobe Commerce

Este artículo proporciona una solución para el problema cuando la optimización de imágenes (IO) rápida está deshabilitada de forma predeterminada con una notificación para ponerse en contacto con Fastly para habilitar la optimización de imágenes. (Fastly Cloud Image Optimizer es un servicio de optimización y manipulación de imágenes en tiempo real que acelera la entrega de imágenes al ofrecer imágenes con un ancho de banda eficiente).

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x

## Problema

En la página Configuración rápida, junto al fragmento de Fastly IO, verá el estado Actual: \_disabled \_with el siguiente mensaje: Póngase en contacto con su representante de ventas o envíe un correo electrónico a `support@fastly.com` para solicitar la activación de optimización de imágenes para su servicio de Fastly.

## Causa

Es posible que el sitio aún no esté activo. Existen procesos para cargar previamente el sitio cuando se ponga en marcha en la base de datos de Fastly.

## Solución

Cree un [ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) y solicite la optimización de imágenes.
