---
title: '"Error "La aplicación del actualizador no está disponible"'
description: Este artículo trata sobre la solución del problema de "la aplicación de actualización no está disponible" que podría tener al intentar actualizar o instalar Adobe Commerce de forma local mediante el Asistente para configuración web.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Error &quot;La aplicación del actualizador no está disponible&quot;

Este artículo trata sobre la solución del problema de &quot;la aplicación de actualización no está disponible&quot; que podría tener al intentar actualizar o instalar Adobe Commerce de forma local mediante el Asistente para configuración web.

## Problema

El siguiente mensaje aparece en la comprobación de disponibilidad:

![Captura de pantalla_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## Productos y versiones afectados

* Adobe Commerce local 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Solución

Para resolver este problema, vea si hay un directorio `<magento_root>/update` que contenga archivos y subdirectorios. De lo contrario, consulta [Configurar el actualizador](https://devdocs.magento.com/guides/v2.3/comp-mgr/updater/update-updater.html) en nuestra documentación para desarrolladores.
