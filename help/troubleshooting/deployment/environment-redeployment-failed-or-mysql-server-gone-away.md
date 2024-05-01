---
title: Error de reimplementación del entorno o el servidor MySQL ha desaparecido
description: Este artículo proporciona una solución para los problemas de Adobe Commerce (todos los métodos de implementación), donde la interrupción del espacio asignado para MySQL causa errores de implementación atascada o conexión a base de datos.
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Error de reimplementación del entorno o el servidor MySQL ha desaparecido

Este artículo proporciona una solución para los problemas de Adobe Commerce (todos los métodos de implementación), donde la interrupción del espacio asignado para MySQL causa errores de implementación atascada o conexión a base de datos.

## Productos y versiones afectados

* Adobe Commerce local y Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Problema

* El proceso de implementación falla con el siguiente error en el registro de implementación (línea de comandos y registro de interfaz de usuario):  ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce responde con un error 503 y se muestra el siguiente mensaje de error en los registros de la aplicación:    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    y aparece el siguiente error al conectarse a un servidor MySQL:    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## Causa

La causa más probable de los problemas es que el espacio asignado a la base de datos MySQL sea demasiado bajo. Para asegurarse de que este es el caso, compruebe el espacio disponible para MySQL como se describe más adelante.

### Compruebe si hay suficiente espacio para MySQL

Para todos los entornos de arquitectura del plan de inicio de Adobe Commerce en la infraestructura en la nube, y [Entorno de integración](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) de la arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube, [SSH para el entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) y ejecute el comando:

```bash
magento-cloud db:size
```

Para el entorno de ensayo o producción de la arquitectura Pro, [SSH para el entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html), y ejecute el `df -h`   `| grep mysql` comando. El resultado será similar al siguiente:

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## Solución

### Para resolver el problema, debe asignar más espacio para MySQL.

Para todos los entornos de integración de arquitectura Starter y arquitectura Pro, esto se hace en la `.magento/services.yaml` , aumentando el valor de `mysql: disk:` parámetro. Por ejemplo:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Consulte la [Configurar el servicio MySQL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html) artículo de referencia.

Para realizar estos cambios en el entorno de ensayo o producción de la arquitectura Pro, debe crear un [Ticket de asistencia](https://support.magento.com). Pero, por lo general, no tendrá que lidiar con esto en Ensayo/Producción de la arquitectura Pro, ya que Adobe Commerce monitoriza estos parámetros por usted y le alerta y/o toma acciones según el contrato.

### Aplicación de los cambios

Una vez que haya cambiado la `.magento/services.yaml` , debe confirmar e insertar los cambios para que se apliquen. La notificación push almacenará en déclencheur el proceso de implementación.
