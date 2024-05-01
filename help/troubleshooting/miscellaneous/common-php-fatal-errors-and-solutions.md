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

*&quot;Error grave de PHP: tiempo de ejecución máximo de 60 segundos superado en....&quot;*

## Solución

Puede actualizar el tiempo máximo de ejecución estableciendo un valor personalizado `max_execution_time` valor en su `php.ini` y volver a implementar.

Por ejemplo:

`max_execution_time = 120`

Consulte la [Personalizar la configuración de php.ini](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) artículo.

## Ejemplo

*&quot;Error grave de PHP: Tamaño de memoria permitido de 792723456 bytes agotado&quot;* (Eso es sólo un ejemplo de tamaño de bytes.)

## Solución

Personalice su `php.ini` configuración. Consulte esto [Personalizar la configuración de php.ini](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) artículo.

## Ejemplo

*&quot;Advertencia de PHP: Desconocido: no se pudo abrir el flujo: no existe el archivo o directorio&quot;*

## Solución

Asegúrese de no quitar los extremos de estilo Windows en la `php.ini` archivo. En Windows, los extremos de línea finalizan con una combinación de un retorno de carro (ASCII 0x0d o \r) y una nueva línea (\n), también denominada CR/LF.

## Ejemplo

*&quot;Error grave de PHP: PDOException no detectada: SQLSTATE\[HY000\] \[1040\] Demasiadas conexiones en&quot;*

## Solución

El entorno MySQL se ha quedado sin espacio en disco. Proporcione más espacio en disco para el entorno MySQL.

## Ejemplo

*&quot;Error grave de PHP: TypeError no capturado: Valor devuelto del Magento&quot;*

## Solución

Compruebe la `<root>/tmp` porque está probablemente lleno. Si está lleno, proporcione más espacio en el directorio. Esto podría implicar simplemente mover archivos a otro directorio o eliminarlos.

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [Errores de configuración de PHP](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [Configuración de PHP requerida](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Verificación de Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [Configurar Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [Error de límite de memoria PHP](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [Soluciones a problemas comunes: límite de memoria](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
