---
title: Error de nivel de anidamiento de función máxima de xdebug de instalación
description: Este artículo proporciona una corrección para el error de nivel máximo de anidación de funciones xdebug durante la instalación.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%
---
# Error de nivel de anidamiento de función máxima de xdebug de instalación

Este artículo proporciona una corrección para el error de nivel máximo de anidación de funciones xdebug durante la instalación.

## Detalles

Durante la instalación de Adobe Commerce, aparece un mensaje similar al siguiente:

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

Se recomienda NO USAR `xdebug` en un entorno de producción.

## Solución

Hay un problema conocido con `xdebug` que puede afectar las instalaciones de Adobe Commerce o el acceso a la tienda o al administrador de Commerce después de la instalación.

Para obtener más información, consulte [Problema conocido con xdebug](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) en nuestra base de conocimiento de soporte.
