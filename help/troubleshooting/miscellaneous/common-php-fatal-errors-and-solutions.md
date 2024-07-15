---
title: Errores y soluciones mortales comunes de PHP
description: Este artículo enumera algunos ejemplos rápidos comunes de errores graves de PHP que puede encontrar al buscar en los registros de Adobe Commerce y las soluciones para los problemas que indican.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Errores y soluciones mortales comunes de PHP

Este artículo enumera algunos ejemplos rápidos comunes de errores graves de PHP que puede encontrar al buscar en los registros de Adobe Commerce y las soluciones para los problemas que indican.

## Ejemplo

*&#39;Error grave de PHP: tiempo de ejecución máximo de 60 segundos superado en....&#39;*

## Solución

Puede actualizar el tiempo máximo de ejecución estableciendo un valor `max_execution_time` personalizado en el archivo `php.ini` y volviendo a implementar.

Por ejemplo:

`max_execution_time = 120`

Consulte el artículo [Personalizar la configuración de php.ini](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html).

## Ejemplo

*&#39;Error grave de PHP: Se agotó el tamaño de memoria permitido de 792723456 bytes&#39;* (Es solo un ejemplo de tamaño de bytes).

## Solución

Personalizar la configuración de `php.ini`. Consulte este artículo [Personalizar la configuración de php.ini](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html).

## Ejemplo

*&#39;Advertencia de PHP: Desconocido: no se pudo abrir el flujo: no existe el archivo o directorio&#39;*

## Solución

Asegúrese de no quitar los extremos de estilo Windows del archivo `php.ini`. En Windows, los extremos de línea finalizan con una combinación de un retorno de carro (ASCII 0x0d o \r) y una nueva línea (\n), también denominada CR/LF.

## Ejemplo

*&#39;Error grave de PHP: PDOException no capturado: SQLSTATE\[HY000\] \[1040\] Demasiadas conexiones en&#39;*

## Solución

El entorno MySQL se ha quedado sin espacio en disco. Proporcione más espacio en disco para el entorno MySQL.

## Ejemplo

*&#39;Error grave de PHP: TypeError no detectado: Valor devuelto del Magento&#39;*

## Solución

Compruebe el directorio `<root>/tmp` porque probablemente esté lleno. Si está lleno, proporcione más espacio en el directorio. Esto podría implicar simplemente mover archivos a otro directorio o eliminarlos.

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [Errores de configuración de PHP](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [Configuración de PHP requerida](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Verificación de Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [Configurar Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [Error de límite de memoria PHP](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [Soluciones a problemas comunes - Límite de memoria](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
