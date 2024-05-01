---
title: El servicio Redis se bloqueó
description: El artículo recomienda cómo corregir Redis.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# El servicio Redis se bloqueó

El artículo recomienda cómo corregir Redis.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.2.x., 2.3.x
* Adobe Commerce local 2.2.x., 2.3x
* Todas las versiones de Redis

## Problema

Lentitud o interrupción del sitio web debido a desbordamiento de memoria en Redis.

## Causa

El desbordamiento de memoria puede provocar que el servicio Redis se bloquee. Durante la hora pico, el servicio Redis puede requerir más memoria que la asignada actualmente.

## Solución

Para comprobar la configuración actual y la memoria utilizada, ejecute el siguiente comando en la CLI. Comprueba la memoria utilizada, la memoria máxima, las claves desalojadas y el tiempo de activación de Redis en días:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

El *REDIS\_PORT* y *REDIS\_HOST* Las variables de se pueden recuperar de `app/etc/env.php`.

Si el resultado de ejecutar la consulta anterior muestra que el porcentaje de memoria libre es inferior al 40 %, [enviar un ticket al servicio de asistencia de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando un aumento de la `maxmemory` en el servidor Redis. Si el valor de claves desalojadas no es &quot;0&quot; o el tiempo de actividad de Redis en días es igual a 0 (lo que indica que Redis se ha bloqueado hoy), también debe [enviar un ticket al servicio de asistencia de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando una investigación y una solución para este problema.

## Lectura relacionada

Para obtener más información sobre la memoria Redis, consulte [Optimización de memoria de Redis](https://redis.io/topics/memory-optimization).
