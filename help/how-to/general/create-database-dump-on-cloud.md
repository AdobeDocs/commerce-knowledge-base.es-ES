---
title: Crear volcado de base de datos en Adobe Commerce en la infraestructura en la nube
description: Este artículo analiza las posibles (y recomendadas) formas de crear un volcado de la base de datos (DB) en Adobe Commerce en la infraestructura en la nube.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 96b145a1f76c296907da96fd97c7a8f7778463f8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Crear volcado de base de datos en Adobe Commerce en la infraestructura en la nube

Este artículo analiza las posibles (y recomendadas) formas de crear un volcado de la base de datos (DB) en Adobe Commerce en la infraestructura en la nube.

Solo necesita utilizar una variante (opción) para volcar la base de datos. Estas opciones se aplican a cualquier tipo de entorno (integración, ensayo, producción) y a cualquier plan (Adobe Commerce en la infraestructura de la nube, arquitectura del plan inicial y Adobe Commerce en la infraestructura de la nube, arquitectura del plan Pro).

## Requisito previo: SSH para su entorno

Para volcar la base de datos en Adobe Commerce en la infraestructura en la nube con cualquier variante de la que se habla en este artículo, primero debe [SSH en su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Tanto si elige la opción 1 como la opción 2, ejecute el comando durante las horas de menor actividad en un nodo secundario de la base de datos.

## Opción 1: db-dump (**ece-tools; recomendado**)

Puede volcar la base de datos con el comando [ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html):

```php
vendor/bin/ece-tools db-dump
```

Esta es la opción recomendada y más segura.

Consulte [Volcar la base de datos (ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) en nuestra Guía de infraestructura de Commerce en la nube.

## Opción 2: mariadb-dump (o mysqldump para versiones anteriores)

+++<b>Para versiones más recientes de MariaDB (11.x y posteriores)</b>

A partir de MariaDB 11.0.1, el enlace simbólico `mysqldump` queda obsoleto. Se recomienda usar `mariadb-dump` en su lugar.

Para obtener más información, consulte [utilidad cliente mariadb-dump](https://mariadb.com/docs/server/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump).

+++

+++<b>Para versiones anteriores de MariaDB</b> 

Si tiene una versión anterior de MariaDB en la que `mariadb-dump` no está disponible, puede volcar la base de datos con el comando nativo MySQL `mysqldump`.

>[!WARNING]
>
>No ejecute este comando en el clúster de base de datos. El clúster no diferenciará si se ejecuta con la base de datos principal o con una secundaria. Si el clúster ejecuta este comando en el principal, la base de datos no podrá ejecutar escrituras hasta que se complete el volcado y esto podría afectar al rendimiento y a la estabilidad del sitio.

Todo el comando puede tener el siguiente aspecto:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

La copia de seguridad de la base de datos creada al ejecutar el comando `mysqldump` y guardada en `\tmp`, debe moverse de esta ubicación. No debería ocupar espacio de almacenamiento en `\tmp` (lo que podría causar problemas).

+++

Para obtener las credenciales de la base de datos (host, nombre de usuario y contraseña), puede llamar a la variable de entorno `MAGENTO_CLOUD_RELATIONSHIPS`:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Documentación relacionada:**

* [mysqldump: un programa de copia de seguridad de la base de datos](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) en la documentación oficial de MySQL.
* [Variables específicas de la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (consulte `MAGENTO_CLOUD_RELATIONSHIPS`) en nuestra Guía de infraestructura de Commerce en la nube.
