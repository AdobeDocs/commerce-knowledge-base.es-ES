---
title: Error durante la implementación al actualizar a la versión compatible con PHP 8.1
description: Este artículo proporciona una solución para el error que se produce durante la implementación al actualizar a una versión compatible con PHP 8.1.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Error durante la implementación al actualizar a la versión compatible con PHP 8.1

Este artículo proporciona una solución para el error que se produce durante la implementación al actualizar a una versión compatible con PHP 8.1.

## Productos y versiones afectados

* Adobe Commerce en la nube 2.4.4. y posterior

* Extensión o tecnología (Fastly, New Relic, etc.) versión PHP 8.1

## Problema

El siguiente error se produce durante la implementación al actualizar a una versión compatible con PHP 8.1.

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## Causa

PHP 8.1 ya incluye soporte JSON y no requiere que la extensión se instale por separado.

## Solución

Elimine JSON de la sección **Runtime** > **Extensions** en `.magento.app.yaml` y vuelva a implementarlo.

## Lectura relacionada

[Aplicación PHP](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/app/php-settings) en nuestra documentación para desarrolladores.
