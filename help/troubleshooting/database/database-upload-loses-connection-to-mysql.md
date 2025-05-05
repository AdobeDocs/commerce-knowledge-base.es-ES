---
title: Carga de base de datos pierde conexión con MySQL
description: Este artículo proporciona una solución para cuando la carga de la base de datos pierde la conexión con MySQL.
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Carga de base de datos pierde conexión con MySQL

Este artículo proporciona una solución para cuando la carga de la base de datos pierde la conexión con MySQL.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube 2.2.x., 2.3.x

## Problema

La base de datos no se carga en ramas principales/de integración en Adobe Commerce en la arquitectura del plan Pro de infraestructura en la nube ni en ninguna rama en Adobe Commerce en la arquitectura del plan inicial de infraestructura en la nube, con el síntoma de que no es posible conectarse. Verá este error en la CLI.

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## Causa

Esto suele deberse a la falta de espacio en disco para importar la base de datos.

## Solución

Compruebe si hay falta de espacio en disco. Para ello, ejecute el comando `netcat` en la CLI con el puerto de base de datos 3306; aparecerá un mensaje de disco lleno si está lleno:

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

Necesitará asignar más espacio para la base de datos en su `services.yaml` e implementarlo si tiene espacio sin utilizar. Para ver los pasos, consulte [Espacio en disco de servicio](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#service-disk-space).

Nota: En el plan de arquitectura Pro, puede comprobar el espacio asignado en la partición ejecutando el siguiente comando: `df -h`

Se espera un resultado similar al siguiente. En este ejemplo, se utilizan 10 GB de los 25 GB asignados y no se utilizan 15 GB de espacio MySQL.

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## Lectura relacionada

[Administrar espacio en disco](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) en nuestra documentación para desarrolladores
