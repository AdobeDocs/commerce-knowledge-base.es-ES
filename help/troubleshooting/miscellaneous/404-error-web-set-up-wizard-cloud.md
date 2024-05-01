---
title: Error 404 no encontrado al acceder al Asistente para configuración web a través del Panel de administración
description: Este artículo proporciona una solución para cuando experimenta un error 404 no encontrado al intentar acceder al Asistente para configuración web a través del panel de administración.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Error 404 no encontrado al acceder al Asistente para configuración web a través del Panel de administración

Este artículo proporciona una solución para cuando experimenta un error 404 no encontrado al intentar acceder al Asistente para configuración web a través del panel de administración.

## Productos y versiones afectados

* La funcionalidad del Asistente para configuración web quedó obsoleta en Adobe Commerce (todos los métodos de implementación) 2.3.6 y se eliminó en 2.4.0.

## Problema

Al instalar una extensión mediante el Asistente para instalación web, se muestra una página 404.

<u>Pasos a seguir</u>:

El comerciante hace clic en el Asistente para instalación web para instalar el nuevo módulo o integración.

<u>Resultado esperado</u>:

Instalaciones de módulo/integración.

<u>Resultado real</u>:

Se muestra un error 404.

## Causa

El Asistente para configuración web se ha deshabilitado para todas las instancias de Adobe Commerce en la infraestructura en la nube, no es posible habilitarlo. Las extensiones deben instalarse mediante Composer.

## Solución

Esta función está desactivada en Adobe Commerce en la infraestructura en la nube.

Consulte [Instalación, administración y actualización de extensiones](https://devdocs.magento.com/cloud/howtos/install-components.html) en nuestra documentación para desarrolladores para obtener información sobre cómo realizar actualizaciones o instalar módulos externos para Adobe Commerce en nuestra infraestructura en la nube.
Consulte [Instalación rápida de](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) en nuestra documentación para desarrolladores para obtener información sobre cómo realizar actualizaciones o instalar módulos externos para Adobe Commerce de forma local.

## Lectura relacionada

* Consulte [Instalación de una extensión](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension) en nuestra documentación para desarrolladores.
