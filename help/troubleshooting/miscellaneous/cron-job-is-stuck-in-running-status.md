---
title: "[!DNL Cron] trabajo está atascado en estado **en ejecución**"
description: Este artículo proporciona soluciones para los casos en los que los trabajos de Adobe Commerce [!DNL cron] no terminan de ejecutarse y persisten en estado de "ejecución", lo que impide que se ejecuten otros  [!DNL cron] trabajos. Esto puede ocurrir por varios motivos, como problemas de red, bloqueos de aplicaciones o problemas de reimplementación.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# El trabajo [!DNL Cron] se ha quedado atascado en el estado &quot;en ejecución&quot;

Este artículo proporciona soluciones cuando los trabajos de Adobe Commerce [!DNL cron] no terminan de ejecutarse y persisten en estado de &quot;ejecución&quot;, lo que impide que se ejecuten otros trabajos de [!DNL cron]. Esto puede ocurrir por varios motivos, como problemas de red, bloqueos de aplicaciones o problemas de reimplementación.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, todas las versiones

## Síntoma {#symptom}

Los síntomas de [!DNL cron] trabajos que deben restablecerse incluyen:

* Aparece una gran cantidad de trabajos en la cola `cron_schedule`
* El rendimiento del sitio empieza a degradarse
* Los trabajos no se ejecutan según lo programado

## Soluciones {#solutions}

### Solución para detener todos los [!DNL cron] trabajos a la vez {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>La ejecución de este comando sin la opción `--job-code` restablece *todos* los trabajos de [!DNL cron], incluidos los que se están ejecutando actualmente, por lo que se recomienda usarlos únicamente en casos excepcionales, como después de comprobar que se deben restablecer todos los trabajos de [!DNL cron]. La reimplementación ejecuta este comando de forma predeterminada para restablecer [!DNL cron] trabajos, de modo que se recuperen correctamente después de realizar la copia de seguridad del entorno. Evite utilizar esta solución cuando se estén ejecutando indexadores.

Para resolver este problema, debe restablecer los trabajos de [!DNL cron] mediante el comando `cron:unlock`. Este comando cambia el estado del trabajo [!DNL cron] en la base de datos y lo finaliza forzosamente para permitir que continúen otros trabajos programados.

1. Abra un terminal y use sus [claves SSH](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/secure-connections) para conectarse al entorno afectado.
1. Obtenga las credenciales de la base de datos MySQL:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Conectar con la base de datos mediante `mysql` :    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. Seleccione la base de datos `main`:    ```shell    use main    ```
1. Buscar todos los trabajos de [!DNL cron] en ejecución:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Copie el `job_code` de cualquier trabajo que se ejecute más de lo normal.
1. Use los identificadores de programación del paso anterior para desbloquear [!DNL cron] trabajos específicos:    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Solución para detener un solo(a) [!DNL cron] {#solution-stop-a-single-cron}

1. Abra un terminal y use sus [claves SSH](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/secure-connections) para conectarse al entorno afectado.
1. Compruebe las tareas de larga ejecución mediante el siguiente comando:

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. En la salida, como en la salida de ejemplo a continuación, verá la fecha actual y la lista de procesos. La columna `START` muestra la fecha y la hora de inicio del proceso:

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. Si ve [!DNL cron] trabajos de larga duración que podrían bloquear el proceso de implementación, puede terminar el proceso con el comando `kill`. Puede identificar el **ID de proceso** (se encontró la columna `PID`) y, a continuación, colocar ese `PID` en el comando para matar el proceso.
El comando **kill process** está:

   ```kill -9 <PID>```

1. A continuación, puede volver a implementar si estaba intentando volver a implementar.
