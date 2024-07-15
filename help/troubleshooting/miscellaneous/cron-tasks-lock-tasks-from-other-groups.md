---
title: Las tareas cron bloquean las tareas de otros grupos
description: Este artículo proporciona una solución para el problema de infraestructura en la nube de Adobe Commerce relacionado con ciertos trabajos cron de larga duración que bloquean otros trabajos cron.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: faa80e8233438fc15781341b3a9d5325269d6d20
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

Cuando abra la tabla de base de datos `cron_schedule`, verá los trabajos con el estado `missed`.

## Causa

Anteriormente, en nuestro entorno de nube, el servidor Jenkins se utilizaba para ejecutar trabajos cron. Jenkins solo ejecutará una instancia de trabajo a la vez; en consecuencia, solo se ejecutará un proceso de `bin/magento cron:run` a la vez.

## Solución

1. Póngase en contacto con el [soporte técnico de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para habilitar los crons autoadministrados.
1. Edite el archivo `.magento.app.yaml` en el directorio raíz del código para Adobe Commerce en la rama de Git. Añada lo siguiente:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Guarde el archivo y las actualizaciones push en los entornos de ensayo y producción (del mismo modo que lo hace para los entornos de integración).

>[!NOTE]
>
>No es necesario transferir configuraciones cron antiguas en las que hay varios `cron:run` presentes en la nueva programación cron; la tarea `cron:run` normal, agregada como se ha descrito anteriormente, es suficiente. Sin embargo, es necesario transferir sus trabajos personalizados si tiene alguno.

### Compruebe si tiene cron autoadministrado habilitado (solo para ensayo y producción de Cloud Pro)

Para comprobar si el cron autoadministrado está habilitado, ejecute el comando `crontab -l` y observe el resultado:

* La cron autoadministrada está habilitada si puede ver las tareas, como se muestra a continuación:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* El cron autoadministrado no está habilitado si no puede ver las tareas y obtener el mensaje de error *&quot;no tiene permiso para usar este programa&quot;*.

>[!NOTE]
>
>El comando mencionado anteriormente para comprobar si el cron autoadministrado está habilitado no se aplica en un plan de inicio y en el entorno de desarrollo/integración.

## Lectura relacionada

* [Configure trabajos cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) en nuestra documentación para desarrolladores.
