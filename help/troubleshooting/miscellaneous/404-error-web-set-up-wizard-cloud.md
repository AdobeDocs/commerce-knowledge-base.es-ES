---
title: Error 404 no encontrado al acceder al Asistente para configuración web a través del Panel de administración
description: Este artículo proporciona una solución para cuando experimenta un error 404 no encontrado al intentar acceder al Asistente para configuración web a través del panel de administración.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Consulte [Instalar, administrar y actualizar extensiones](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure-store/extensions) en nuestra documentación para desarrolladores para obtener información sobre cómo realizar actualizaciones o instalar módulos externos para Adobe Commerce en nuestra infraestructura en la nube.
Consulte [Instalación rápida](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/composer) en nuestra documentación para desarrolladores para obtener información sobre cómo realizar actualizaciones o instalar módulos externos para Adobe Commerce local.

## Lectura relacionada

* Consulte [Instalar una extensión](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension) en nuestra documentación para desarrolladores.
