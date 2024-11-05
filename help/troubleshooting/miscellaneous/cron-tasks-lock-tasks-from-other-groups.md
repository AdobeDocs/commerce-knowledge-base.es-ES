---
title: '[!DNL Cron] tareas bloquean tareas de otros grupos'
description: Este artículo proporciona una solución para el problema de infraestructura en la nube de Adobe Commerce relacionado con ciertos  [!DNL cron] trabajos de largo plazo que bloquean otros [!DNL cron] trabajos.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# [!DNL Cron] tareas bloquean tareas de otros grupos

Este artículo proporciona una solución para el problema de infraestructura en la nube de Adobe Commerce relacionado con ciertos trabajos de [!DNL cron] de larga duración que bloquean otros [!DNL cron] trabajos.

## Productos y versiones afectados

* Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube
* Incorporación antes de mayo de 2019

## Problema

En Adobe Commerce para la nube, cuando tiene [!DNL cron] tareas complejas (tareas de larga ejecución), podrían bloquear otras tareas para su ejecución. Por ejemplo, la tarea de los indexadores reindexa los indexadores invalidados. Puede tardar unas horas en finalizar y bloqueará otros trabajos predeterminados de [!DNL cron], como el envío de correos electrónicos, la generación de mapas del sitio, las notificaciones a los clientes y otras tareas personalizadas.

<u>Síntomas</u>:

No se realizan los procesos ejecutados por [!DNL cron] trabajos. Por ejemplo, las actualizaciones de productos no se aplican durante horas o los clientes informan que no reciben correos electrónicos.

Cuando abra la tabla de base de datos `cron_schedule`, verá los trabajos con el estado `missed`.

## Causa

Anteriormente, en nuestro entorno de nube, el servidor Jenkins se usaba para ejecutar [!DNL cron] trabajos. Jenkins solo ejecutará una instancia de trabajo a la vez; en consecuencia, solo se ejecutará un proceso de `bin/magento cron:run` a la vez.

## Solución

1. Póngase en contacto con el [soporte técnico de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para habilitar [!DNL crons] administrado automáticamente.
1. Edite el archivo `.magento.app.yaml` en el directorio raíz del código para Adobe Commerce en la rama [!DNL Git]. Añada lo siguiente:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Guarde el archivo y las actualizaciones push en los entornos de ensayo y producción (del mismo modo que lo hace para los entornos de integración).

>[!NOTE]
>
>No es necesario transferir las configuraciones antiguas [!DNL cron] en las que hay varios `cron:run` presentes en la nueva programación [!DNL cron]; la tarea normal `cron:run`, agregada como se ha descrito anteriormente, es suficiente. Sin embargo, es necesario transferir sus trabajos personalizados si tiene alguno.

### Compruebe si tiene habilitado [!DNL cron] administrado automáticamente (solo para ensayo y producción de Cloud Pro)

Para comprobar si el [!DNL cron] administrado automáticamente está habilitado, ejecute el comando `crontab -l` y observe el resultado:

* [!DNL cron] administrado automáticamente está habilitado si puede ver las tareas como las siguientes:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* El [!DNL cron] autoadministrado no está habilitado si no puede ver las tareas y obtener el mensaje de error *&quot;no tiene permiso para usar este programa&quot;*.

>[!NOTE]
>
>El comando mencionado anteriormente para comprobar si la función autoadministrada [!DNL cron] está habilitada no se aplica en un plan de inicio ni en el entorno de desarrollo/integración.

## Lectura relacionada

* [Configurar [!DNL cron] trabajos](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) en nuestra documentación para desarrolladores
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
