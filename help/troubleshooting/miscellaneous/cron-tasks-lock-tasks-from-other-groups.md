---
title: Las tareas cron bloquean las tareas de otros grupos
description: Este artículo proporciona una solución para el problema de infraestructura en la nube de Adobe Commerce relacionado con ciertos trabajos cron de larga duración que bloquean otros trabajos cron.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Las tareas cron bloquean las tareas de otros grupos

Este artículo proporciona una solución para el problema de infraestructura en la nube de Adobe Commerce relacionado con ciertos trabajos cron de larga duración que bloquean otros trabajos cron.

## Productos y versiones afectados

* Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube
* Incorporación antes de mayo de 2019

## Problema

En Adobe Commerce para la nube, cuando tiene tareas cron complejas (tareas de larga ejecución), pueden bloquear otras tareas para su ejecución. Por ejemplo, la tarea de los indexadores reindexa los indexadores invalidados. Puede tardar unas horas en terminar y bloqueará otros trabajos cron predeterminados, como el envío de correos electrónicos, la generación de mapas del sitio, las notificaciones a los clientes y otras tareas personalizadas.

<u>Síntomas</u>:

Los procesos ejecutados por los trabajos cron no se realizan. Por ejemplo, las actualizaciones de productos no se aplican durante horas o los clientes informan que no reciben correos electrónicos.

Al abrir el `cron_schedule` tabla de la base de datos, verá los trabajos con `missed` estado.

## Causa

Anteriormente, en nuestro entorno de nube, el servidor Jenkins se utilizaba para ejecutar trabajos cron. Jenkins solo ejecutará una instancia de un trabajo a la vez; en consecuencia, solo habrá una `bin/magento cron:run` el proceso se ejecuta a la vez.

## Solución

1. Contacto [Compatibilidad con Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para tener crons autoadministrados habilitados.
1. Edite el `.magento.app.yaml` en el directorio raíz del código para Adobe Commerce en la rama de Git. Añada lo siguiente:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Guarde el archivo y las actualizaciones push en los entornos de ensayo y producción (del mismo modo que lo hace para los entornos de integración).

>[!NOTE]
>
>No es necesario transferir configuraciones cron antiguas en las que haya varias `cron:run` están presentes en la nueva programación de cron; el `cron:run` La tarea de, añadida como se ha descrito anteriormente, es suficiente. Sin embargo, es necesario transferir sus trabajos personalizados si tiene alguno.

### Compruebe si tiene cron autoadministrado habilitado (solo para ensayo y producción de Cloud Pro)

Para comprobar si el cron autoadministrado está habilitado, ejecute el `crontab -l` y observe el resultado:

* La cron autoadministrada está habilitada si puede ver las tareas, como se muestra a continuación:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* El cron autogestionado no está habilitado si no puede ver las tareas y obtener el *&quot;no tiene permiso para utilizar este programa&quot;* mensaje de error.

>[!NOTE]
>
>El comando mencionado anteriormente para comprobar si el cron autoadministrado está habilitado no se aplica en un plan de inicio y en el entorno de desarrollo/integración.

## Lectura relacionada

* [Configuración de trabajos cron](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html) en nuestra documentación para desarrolladores
