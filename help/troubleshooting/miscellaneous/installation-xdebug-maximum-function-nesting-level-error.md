---
title: Error de nivel de anidamiento de función máxima de xdebug de instalación
description: Este artículo proporciona una corrección para el error de nivel máximo de anidación de funciones xdebug durante la instalación.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# Error de nivel de anidamiento de función máxima de xdebug de instalación

Este artículo proporciona una corrección para el error de nivel máximo de anidación de funciones xdebug durante la instalación.

## Detalles

Durante la instalación de Adobe Commerce, aparece un mensaje similar al siguiente:

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

Se recomienda encarecidamente que NO USE `xdebug` en un entorno de producción.

## Solución

Hay un problema conocido con `xdebug` que pueden afectar a las instalaciones de Adobe Commerce o al acceso a la tienda o al administrador de Commerce después de la instalación.

Para obtener más información, consulte [Problema conocido con xdebug](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) en nuestra base de conocimiento de soporte.
