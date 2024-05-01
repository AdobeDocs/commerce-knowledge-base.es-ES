---
title: Solucionador de problemas de Redis en Adobe Commerce
description: Este artículo es una herramienta para solucionar problemas de los comerciantes de infraestructura en la nube de Adobe Commerce local y Adobe Commerce que tienen problemas con Redis. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas. Según los síntomas y la configuración, el solucionador de problemas explicará cómo solucionar problemas de versión y memoria y optimizar el rendimiento.
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Solucionador de problemas de Redis en Adobe Commerce

Este artículo es una herramienta para solucionar problemas de los comerciantes de infraestructura en la nube de Adobe Commerce local y Adobe Commerce que tienen problemas con Redis. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas. Según los síntomas, el solucionador de problemas le explicará cómo puede solucionar problemas de versión y memoria y optimizar el rendimiento.

## Paso 1: Problema de Redis {#step-1}

+++Problema con Redis?

a. SÍ: Continúe con [Paso 2](#step2)</a>.

b. NO: Volver a [support.magento.com](https://support.magento.com/hc/en-us) y busque los artículos de solución de problemas relevantes.

+++

## Paso 2: Confirmación de los parches Redis instalados {#step-2}

+++¿Se instalaron los parches actuales de Redis?

a. SÍ: Continúe con [Paso 3](#step3)</a>.

b. NO - Asegúrese de que tiene la última versión del paquete `magento-cloud-patches` instalado. Este paquete tiene los parches necesarios para Redis. Para acceder, vaya a [Parches de nube de magneto de GitHub](https://github.com/magento/magento-cloud-patches/).

+++

## Paso 3: Confirmar que la versión de Redis es compatible {#step-3}

+++¿En las versiones 3.2 o 5.0 de Redis?

Realice la comprobación ejecutando los siguientes comandos en la CLI. Pro o Staging: `$ redis-cli -p %port-number% info | grep redis_version`, donde `%port-number%` es el número del puerto, que se puede encontrar en la variable `app/etc/env.php` o ejecutando uno de estos comandos: `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` o `$ cat app/etc/env.php | grep redis -A 3` Inicio o integración: `$ redis-cli -h 'redis.internal' info | grep redis_version`

a. SÍ: Continúe con [Paso 4](#step4).

b. NO: Adobe Commerce es compatible con las versiones 3.2 y 5.0 de Redis. Si está ejecutando Adobe Commerce en la infraestructura en la nube 2.3.3 o superior, le recomendamos que actualice a Redis 5. Para ver los pasos de configuración de la arquitectura de planificación, integración y entornos iniciales de Adobe Commerce en la infraestructura en la nube, incluida la rama maestra, consulte [Adobe Commerce en la infraestructura de la nube > Configuración del servicio Redis](https://devdocs.magento.com/cloud/project/services-redis.html)</a> en nuestra documentación para desarrolladores. **Debe [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para cambiar la configuración del servicio en los entornos de producción y ensayo de la arquitectura Pro. Además, para Adobe Commerce en la infraestructura en la nube y Adobe Commerce local 2.3.5+, se recomienda la implementación de caché de Redis extendida. Este tipo de implementación de caché de Redis proporciona mejoras que minimizan el número de consultas a Redis que se realizan en cada solicitud de Adobe Commerce. Para ver los pasos, consulte [Implementación de caché de Redis extendida en Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) en nuestra base de conocimiento de soporte. Para el resto de usuarios de Adobe Commerce, consulte [Guía de configuración de Adobe Commerce > Configuración de Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) en nuestra documentación para desarrolladores, para ver los pasos.

+++

## Paso 4: Verificar la última versión de ECE-Tools {#step-4}

+++¿Tiene la versión más reciente de [Herramientas ECE > v2002.1.1](https://github.com/magento/ece-tools/releases)?

Compruebe qué versión tiene ejecutando el comando en CLI/Terminal: `$php vendor/bin/composer info magento/ece-tools`.

a. SÍ: Continúe con [Paso 5](#step5).

b. NO - [Actualizar ECE-Tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html) a la última versión.

+++

## Paso 5: Evaluación del tráfico de red {#step-5}

+++¿Hay mucho tráfico de red entre la aplicación y Redis?

a. SÍ: pruebe lo siguiente: Para una arquitectura no dividida, asegúrese de que [conexión secundaria](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) se utiliza. Para la arquitectura dividida, la variable [La caché L2 debe estar habilitada](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b. NO: configurar la caché L2 mediante [Actualizando servidor de Redis](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). Continúe en [Paso 6](#step6).

+++

## Paso 6: Comprobación de la velocidad del sitio {#step-6}

+++¿Sigue funcionando el sitio lentamente, después de habilitar la caché L2?

a. SÍ: compruebe el directorio temporal `/dev/shm` para ver si necesitas aumentar el espacio. Si necesitas más espacio, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b. NO: Al habilitar la caché L2, parece que se han resuelto los problemas de Redis.

+++

[Volver al paso 1](#step-1)
