---
title: "[!DNL Cron] el trabajo está atascado en el estado **en ejecución**"
description: Este artículo proporciona soluciones para cuando Adobe Commerce [!DNL cron] los trabajos no terminan de ejecutarse y persisten en estado de "ejecución", lo que impide que otros [!DNL cron] trabajos en ejecución. Esto puede ocurrir por varios motivos, como problemas de red, bloqueos de aplicaciones o problemas de reimplementación.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron] el trabajo está atascado en estado &quot;en ejecución&quot;

Este artículo proporciona soluciones para cuando Adobe Commerce [!DNL cron] los trabajos no terminan de ejecutarse y persisten en estado de &quot;ejecución&quot;, lo que impide que otros [!DNL cron] trabajos en ejecución. Esto puede ocurrir por varios motivos, como problemas de red, bloqueos de aplicaciones o problemas de reimplementación.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube, todas las versiones

## Síntoma {#symptom}

Síntomas de [!DNL cron] los trabajos que se deben restablecer incluyen:

* Aparece una gran cantidad de trabajos en `cron_schedule` cola
* El rendimiento del sitio empieza a degradarse
* Los trabajos no se ejecutan según lo programado

## Soluciones {#solutions}

### Solución para detener todo [!DNL cron] trabajos a la vez {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>Ejecutar este comando sin el `--job-code` restablecimientos de opción *todo* [!DNL cron] trabajos, incluidos los que se están ejecutando actualmente, por lo que recomendamos utilizarlo solo en casos excepcionales, como después de comprobar que todos los [!DNL cron] se deben restablecer los trabajos. Volver a implementar ejecuta este comando de forma predeterminada para restablecer [!DNL cron] trabajos, de modo que se recuperen correctamente después de que el entorno se haya vuelto a crear. Evite utilizar esta solución cuando se estén ejecutando indexadores.

Para resolver este problema, debe restablecer el [!DNL cron] trabajos que utilizan el `cron:unlock` comando. Este comando cambia el estado del [!DNL cron] trabajo en la base de datos, finalizando el trabajo a la fuerza para permitir que continúen otros trabajos programados.

1. Abra un terminal y use su [Claves SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) para conectarse al entorno afectado.
1. Obtenga las credenciales de la base de datos MySQL:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Conexión a la base de datos mediante `mysql` :    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. Seleccione el `main` base de datos:    ```shell    use main    ```
1. Buscar todos los recursos en ejecución [!DNL cron] trabajos:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Copie el `job_code` de cualquier trabajo que dure más de lo normal.
1. Utilice los ID de programación del paso anterior para desbloquear elementos específicos [!DNL cron] trabajos:    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Solución para detener un único [!DNL cron] {#solution-stop-a-single-cron}

1. Abra un terminal y use su [Claves SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) para conectarse al entorno afectado.
1. Compruebe las tareas de larga ejecución mediante el siguiente comando:

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. En la salida, como en la salida de ejemplo a continuación, verá la fecha actual y la lista de procesos. El `START` La columna muestra la fecha y la hora de inicio del proceso:

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

1. Si ve una carrera larga [!DNL cron] trabajos que pueden bloquear el proceso de implementación, puede terminar el proceso utilizando la variable `kill` comando. Puede identificar el **ID de proceso** (se encontró el `PID` ), y luego ponga eso `PID` en el comando para cerrar el proceso.
El **proceso de eliminación** el comando es:

   ```kill -9 <PID>```

1. A continuación, puede volver a implementar si estaba intentando volver a implementar.
