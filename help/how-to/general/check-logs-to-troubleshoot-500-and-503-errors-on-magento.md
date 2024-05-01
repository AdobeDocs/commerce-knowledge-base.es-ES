---
title: Compruebe los registros para solucionar errores 500 y 503 en Adobe Commerce
description: Este artículo explica cómo comprobar el "access.log" y los registros relacionados para solucionar los errores 503 y 500, que pueden deberse al tráfico o a recursos insuficientes del servidor. La visualización de access.log y los registros relacionados puede proporcionar información sobre lo que puede estar causando problemas relacionados con Adobe Commerce en la infraestructura en la nube.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Compruebe los registros para solucionar errores 500 y 503 en Adobe Commerce

Este artículo explica cómo comprobar la `access.log` y los registros relacionados para solucionar los errores 503 y 500, que pueden deberse al tráfico o a recursos insuficientes del servidor. Visualización de la `access.log` y los registros relacionados pueden proporcionar información sobre lo que puede estar causando problemas relacionados con Adobe Commerce en la infraestructura en la nube.

<!--
Bob - not in TOC
-->

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todo [versiones compatibles](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Para ver los registros de estos errores de servidor, consulte la `access.log` en el servidor web, por ejemplo,. `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Para comprobar los registros relacionados:

1. Ejecute el siguiente comando en la CLI si se encuentra en el día actual (para la arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube). O hasta un momento determinado del pasado (en el caso de Adobe Commerce en la infraestructura de la nube o la arquitectura del plan inicial), ya que la duración de la cobertura de los registros es limitada y la rotación de registros no está disponible: `grep -r "\" [50[0-9]" /path/to/access.log` Si el error se ha producido en el pasado, ejecute el siguiente comando en la CLI (solo para la arquitectura Pro): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. A continuación, compruebe la `exception.log` y `error.log` o su equivalente [registro girado](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) (registros que se giran y comprimen automáticamente cuando alcanzan un determinado tamaño de archivo) para la misma marca de tiempo para localizar el posible error y ver qué puede haber ocurrido para ocasionarlo. Nota: Para comprobar la `exception.log` y `error.log` ejecute los comandos anteriores en la CLI pero reemplace `access.log` con `exception.log` o `error.log`.

## Lectura relacionada

* Consulte [Visualización y administración de registros](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) en el *Guía de Adobe Commerce sobre infraestructura en la nube*.
* Consulte [Solución de problemas con errores 503](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) en nuestra base de conocimiento de soporte.
* Consulte [Solucionador de problemas de Magento Site Down](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) en nuestra base de conocimiento de soporte.
