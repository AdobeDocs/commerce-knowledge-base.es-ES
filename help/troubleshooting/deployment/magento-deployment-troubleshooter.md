---
title: Solucionador de problemas de implementación de Adobe Commerce
description: Las implementaciones atascadas y las implementaciones fallidas en Adobe Commerce se pueden resolver con la herramienta Solucionador de problemas de implementación. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 4704446d043e3175b5af27c068908e58bfb7a9ff
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# Solucionador de problemas de implementación de Adobe Commerce

Las implementaciones atascadas y las implementaciones fallidas en Adobe Commerce se pueden resolver con la herramienta Solucionador de problemas de implementación. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas.

## Paso 1: Verificación de que el servicio se está ejecutando {#step-1}

+++**¿Adobe Commerce está en servicio de infraestructura en la nube?**

Implementación atascada: ¿Adobe Commerce está funcionando en el servicio de infraestructura en la nube? Compruebe [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. SÍ - Continúe con [Paso 2](#step-2).\
b. NO - Mantenimiento o cortes globales. Consulte la duración estimada y las actualizaciones.

+++

## Paso 2: Comprobación de implementaciones en otros entornos {#step-2}

+++**¿Hay implementaciones en otros entornos que bloquean la implementación en el entorno existente?**

Para obtener una lista de las actividades en curso, ejecute el siguiente comando usando la CLI de Magento en la nube (si solo se le ha agregado a un proyecto en la nube). **Nota**: Compruebe que se encuentra en la versión más reciente de la CLI de Magento en la nube. Para ver los pasos, consulte [Actualizar la CLI](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/cloud-cli/cloud-cli-overview) en la guía de Commerce en infraestructura de nube.

```bash
magento-cloud --state=in_progress
```

Para obtener una lista de las actividades en curso, ejecute el siguiente comando mediante la CLI de Magento en la nube (si se le ha agregado a varios proyectos):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Para encontrar información sobre una actividad de implementación existente (consulte [Comprobación del registro de implementación si la interfaz de usuario de la nube tiene el error &quot;Recorte de registro&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
para obtener más información) puede ejecutar este comando para obtener un registro en ejecución de esa actividad:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. SÍ: solucionar problemas del otro entorno que bloquea la implementación en el entorno existente. Continúe con [Paso 3](#step-3).

b. NO - Solucionar problemas del entorno actual. Continúe con [Paso 3](#step-3).

+++


## Paso 3: Verificación de SSH en todos los nodos {#step-3}

+++**SSH correcto para todos los nodos?**

a. SÍ - Continúe con [Paso 4](#step-4).\
b. NO - [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Paso 4: Verificación de todos los servicios que se ejecutan {#step-4}

+++**Todos los servicios en ejecución?**

a. SÍ - Continúe con [Paso 5](#step-5).\
b. NO - [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Paso 5: Verificar la ejecución de Bitbucket {#step-5}

+++**Usando Bitbucket?**

a. SÍ: comprobar [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO - Comprobar errores de registro de implementación en [Generar e implementar registros](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations). Continúe con [Paso 6](#step-6).

+++

## Paso 6: Comprobación de los códigos de error {#step-6}

+++**¿Código de error notificado?**

a. SÍ - Continúe con [Paso 7](#step-7).\
b. NO - Continúe con [Paso 8](#step-8).

+++

## Paso 7: Error 403 prohibido {#step-7}

+++**403 prohibido?**

a. SÍ - Continúe con [Paso 16](#step-16).
b. NO - Continúe con [Paso 9](#step-9).

+++

## Paso 8: Verificación de los trabajos cron en ejecución {#step-8}

+++**¿Se están ejecutando actualmente los trabajos cron?**: inicia sesión mediante ssh en la rama y ejecuta `ps aufxx |grep cron`.

a. SÍ: inicie sesión mediante ssh en la rama afectada (por ejemplo, la principal). Mata y desbloquea trabajos cron. Esto eliminará los trabajos de cron y restablecerá el estado. Ejecute `php vendor/bin/ece-tools cron:kill` y luego `php vendor/bin/ece-tools cron:unlock`. Si estaba en el proceso de combinar un entorno en otro, compruebe ambos entornos para ejecutar crons.\
b. NO - Continúe con [Paso 17](#step-17).

+++

## Paso 9: Error de la aplicación implementable en el clúster remoto {#step-9}

+++**Error al cargar la aplicación en el clúster remoto?**

a. SÍ - Continúe con [Paso 10](#step-10).\
b. NO - Continúe con [Paso 11](#step-11).

+++

## Paso 10: Comprobar que haya suficiente almacenamiento {#step-10}

+++**¿Almacenamiento disponible está bien?**

a. SÍ - Continúe con [Paso 11](#step-11).\
b. NO - Revisar [Administrar espacio en disco](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space).

+++

## Paso 11: Verificación del espacio en disco {#step-11}

+++**_No se pudo escribir el archivo. Advertencia _?**

a. SÍ: [aumente el valor del disco en .magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) y vuelva a implementarlo. Si esto no funciona, [envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Continúe con [Paso 12](#step-12).

+++

## Paso 12: Error de reimplementación del entorno {#step-12}

+++**Error de reimplementación de entorno?**

a. SÍ - Continúe con [Paso 13](#step-13).\
b. NO - Continúe con [Paso 8](#step-8).

+++

## Paso 13: Error al comprobar la actualización de Elasticsearch {#step-13}

+++¿Se está actualizando o implementando **Elasticsearch?**

a. SÍ: pasos de actualización erróneos de Elasticsearch. Consulte [Compatibilidad de software de Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Si la actualización de Elasticsearch sigue sin funcionar, [envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Nota**: en Adobe Commerce en la infraestructura en la nube, tenga en cuenta que las actualizaciones de servicios no se pueden insertar en el entorno de producción sin un aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro del periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Así que 48 horas antes de que tus cambios deban estar en producción, [envía un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detallando tu actualización de servicio requerida e indicando la hora en que quieres que comience el proceso de actualización.\
b. NO - Continúe con [Paso 14](#step-14).

+++

## Paso 14: Comprobación de los límites de espacio {#step-14}

+++**Sistema de archivos sin nodos o espacio?**

a. SÍ: consulte [Administrar espacio en disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NO - Continúe con [Paso 15](#step-15).

+++

## Paso 15: Error de versión de Elasticsearch {#step-15}

+++**¿Error sobre las versiones de Elasticsearch?**

a. SÍ - Continúe con [Paso 16](#step-16).\
b. NO - Continúe con [Paso 21](#step-21).

+++

## Paso 16: Verificar la configuración del compositor {#step-16}

+++**Configuración del compositor correcta?**

a. SÍ - Continúe con [Paso 10](#step-10).\
b. NO - Revisar [página web del Solucionador de problemas del compositor](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Paso 17: Comprobación de procesos de larga duración {#step-17}

+++**Procesos de larga duración?**

a. SÍ: identifique los procesos de larga ejecución y luego elimine los procesos:
1. Ejecute el siguiente comando en el terminal: `ps aufx`.
1. Busque el PID del proceso de larga duración.
1. Finalice el proceso mediante `kill -9 <PID>`.

Supervise las implementaciones para que vuelvan a producirse.

b. NO - Continúe con [Paso 18](#step-18).

+++

## Paso 18: Compruebe si hay algún fallo en el gancho posterior {#step-18}

+++**Error/bloqueo del gancho de publicación?**

a. SÍ - Base de datos: [Espacio libre en disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), tablas dañadas o incompletas.\
b. NO - Continúe con [Paso 19](#step-19).

+++

## Paso 19: Compruebe si las extensiones de terceros bloquean la implementación {#step-19}

+++**Usar extensiones de terceros?**

a. SÍ: intente [deshabilitar las extensiones de terceros](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/extensions) y ejecutar la implementación (para ver si son la causa del problema), especialmente si hay nombres de extensión en algún error.\
b. NO - Continúe con [Paso 20](#step-20).

+++

## Paso 20: Comprobación de consultas lentas {#step-20}

+++**¿Consultas de larga duración?**

[Compruebe el registro de consultas lentas y MySQL show processlist](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. SÍ: elimine todas las consultas de larga duración. Revisar [Sintaxis de MySQL Kill.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NO - [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Paso 21: Versión anterior de Elasticsearch {#step-21}

+++**Desactualizando versiones de Elasticsearch?**

a. SÍ: no se puede realizar mediante la configuración. [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Volver al paso 1](#step-1)
