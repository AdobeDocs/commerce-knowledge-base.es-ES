---
title: Error durante la implementación al actualizar a la versión compatible con PHP 8.1
description: Este artículo proporciona una solución para el error que se produce durante la implementación al actualizar a una versión compatible con PHP 8.1.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%
---
# Error durante la implementación al actualizar a la versión compatible con PHP 8.1

Este artículo proporciona una solución para el error que se produce durante la implementación al actualizar a una versión compatible con PHP 8.1.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube 2.4.4. y más tarde

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
