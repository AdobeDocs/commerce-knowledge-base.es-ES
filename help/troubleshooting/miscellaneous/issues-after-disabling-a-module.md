---
title: Problemas después de deshabilitar un módulo
description: Este artículo proporciona una solución para los problemas de funcionalidad del módulo después de haber deshabilitado la salida del módulo en el administrador de Commerce.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Problemas después de deshabilitar un módulo

Este artículo proporciona una solución para los problemas de funcionalidad del módulo después de haber deshabilitado la salida del módulo en el administrador de Commerce.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube 2.1.X o anterior
* Adobe Commerce local 2.1.X o anterior

## Problema

Después de deshabilitar la salida del módulo en el administrador de Commerce, en **Tiendas** > **Configuración** > **Configuración** > AVANZADA > **Avanzada**, es posible que empiece a ver problemas relacionados con la funcionalidad del módulo.

## Causa

Al deshabilitar una salida de módulo en **Almacenes** > **Configuración** > **Configuración** > AVANZADA > **Avanzada**, solo se deshabilita la salida (HTML, JS), pero no la funcionalidad de este módulo.

## Solución

Si necesita deshabilitar la funcionalidad del módulo, deshabilite el módulo tal como se describe en [Habilitar o deshabilitar módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/manage-modules) en nuestra documentación para desarrolladores.

La funcionalidad de deshabilitación de la salida del módulo se eliminó a partir de la versión 2.2.0.
