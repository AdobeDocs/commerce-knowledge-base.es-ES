---
title: Compruebe los registros para solucionar errores 500 y 503 en Adobe Commerce
description: Este artículo explica cómo comprobar el "access.log" y los registros relacionados para solucionar los errores 503 y 500, que pueden deberse al tráfico o a recursos insuficientes del servidor. La visualización de access.log y los registros relacionados puede proporcionar información sobre lo que puede estar causando problemas relacionados con Adobe Commerce en la infraestructura en la nube.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: 66ac9de94e9a4a1eccdb5aac1875ecf0a0637e90
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Compruebe los registros para solucionar errores 500 y 503 en Adobe Commerce

Este artículo explica cómo comprobar `access.log` y los registros relacionados para solucionar errores 503 y 500, que pueden deberse al tráfico o a recursos insuficientes del servidor. Ver `access.log` y los registros relacionados puede proporcionar información sobre lo que puede estar causando problemas relacionados con Adobe Commerce en la infraestructura de la nube.

<!--
Bob - not in TOC
-->

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas [versiones compatibles](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Para ver los registros de estos errores del servidor, compruebe `access.log` en el servidor web, por ejemplo, `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Para comprobar los registros relacionados:

1. Ejecute el siguiente comando en la CLI si se encuentra en el día actual (para la arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube). O hasta cierto punto en el pasado (en el caso de Adobe Commerce en la infraestructura de la nube con la arquitectura del plan inicial), ya que la duración de la cobertura de los registros es limitada y la rotación de registros no está disponible: `grep -r "\" [50[0-9]" /path/to/access.log` Si el error se ha producido en el pasado, ejecute el siguiente comando en la CLI (solo arquitectura Pro): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. A continuación, compruebe `exception.log` y `error.log` o el registro girado [3&rbrace; equivalente (registros que se giran y se comprimen automáticamente cuando alcanzan un determinado tamaño de archivo) para la misma marca de tiempo a fin de localizar el posible error y ver qué pudo haber causado. ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) Nota: Para comprobar `exception.log` y `error.log`, ejecute los comandos anteriores en la CLI, pero reemplace `access.log` por `exception.log` o `error.log`.

## Lectura relacionada

* Consulte [Ver y administrar registros](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) en la *Guía de infraestructura en la nube de Adobe Commerce*.
* Ver [Solución de problemas de 503 errores](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) en nuestra base de conocimiento de asistencia.