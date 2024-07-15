---
title: Habilitar caché para evitar la degradación del rendimiento
description: Este artículo explica cómo resolver un problema de sitio lento causado por la deshabilitación de ciertos tipos de caché de Adobe Commerce.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Habilitar caché para evitar la degradación del rendimiento

Este artículo explica cómo resolver un problema de sitio lento causado por la deshabilitación de ciertos tipos de caché de Adobe Commerce.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* Adobe Commerce local 2.2.x, 2.3.x

## Problema

Observará una degradación del rendimiento. Por ejemplo, la página Cierre de compra se carga lentamente o el valor Apdex disminuye en New Relic.

## Causa

Una razón para la degradación del rendimiento puede ser que se deshabiliten ciertos tipos de caché de Adobe Commerce.

## Solución

1. En primer lugar, compruebe el estado de la caché de Adobe Commerce para ver si este es el problema. Para ello, [SSH a su entorno](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) y ejecute el siguiente comando:

   ```bash
   php bin/magento cache:status
   ```

   Esto mostraría el estado de cada tipo de caché (&quot;0&quot; para deshabilitado, &quot;1&quot; para habilitado). O puede obtener esta información en el archivo `app/etc/env.php`.

1. Investigue los tipos de caché deshabilitados. Todos los tipos de caché de Adobe Commerce deben habilitarse, a menos que haya recibido instrucciones alternativas de Adobe. Las extensiones de terceros no deben requerir la desactivación de la caché de Adobe Commerce.
1. Si la investigación confirma que algunos tipos de caché están deshabilitados por error, actívelos ejecutando el siguiente comando para cada tipo de caché: `php bin/magento cache:enable <your_disabled_cache_type>`

Si tiene dudas o preguntas sobre si cierto tipo de caché de Adobe Commerce se puede o se debe deshabilitar, [póngase en contacto con el servicio de atención al cliente de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para obtener recomendaciones.

## Lectura relacionada

Documentación de la caché de Adobe Commerce en nuestra documentación para desarrolladores:

* [Resumen de caché de Adobe Commerce](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html)
* [Administrar la caché](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cache.html)

Otros posibles motivos de los problemas de rendimiento y sus soluciones:

* [Deshabilitar la salida del titular de Adobe Commerce para mejorar el rendimiento del sitio](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)
* [Las tablas MySQL son demasiado grandes](/help/troubleshooting/database/mysql-tables-are-too-large.md)
* [Lento rendimiento, crons lentos y de larga duración](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Acceso de administrador restringido que causa problemas de rendimiento](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
