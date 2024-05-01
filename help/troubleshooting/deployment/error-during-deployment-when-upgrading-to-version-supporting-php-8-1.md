---
title: Error durante la implementación al actualizar a la versión compatible con PHP 8.1
description: Este artículo proporciona una solución para el error que se produce durante la implementación al actualizar a una versión compatible con PHP 8.1.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
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

Eliminar JSON de **Runtime** > **Extensiones** sección en `.magento.app.yaml` y vuelva a implementarlo.

## Lectura relacionada

[aplicación PHP](https://devdocs.magento.com/cloud/project/magento-app-php-application.html) en nuestra documentación para desarrolladores.
