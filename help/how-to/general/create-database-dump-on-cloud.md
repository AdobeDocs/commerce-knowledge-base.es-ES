---
title: Crear volcado de base de datos en Adobe Commerce en la infraestructura en la nube
description: Este artículo analiza las posibles (y recomendadas) formas de crear un volcado de la base de datos (DB) en Adobe Commerce en la infraestructura en la nube.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 0948b2a94ee4f2a355e7c024a09929f0ad223783
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Crear volcado de base de datos en Adobe Commerce en la infraestructura en la nube

Este artículo analiza las posibles (y recomendadas) formas de crear un volcado de la base de datos (DB) en Adobe Commerce en la infraestructura en la nube.

Solo necesita utilizar una variante (opción) para volcar la base de datos. Estas opciones se aplican a cualquier tipo de entorno (integración, ensayo, producción) y a cualquier plan (Adobe Commerce en la infraestructura de la nube, arquitectura del plan inicial y Adobe Commerce en la infraestructura de la nube, arquitectura del plan Pro).

## Requisito previo: SSH para su entorno

Para volcar la base de datos en Adobe Commerce en la infraestructura en la nube con cualquier variante tratada en este artículo, primero debe [SSH a su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Tanto si elige la opción 1 como la opción 2, ejecute el comando durante las horas de menor actividad en un nodo secundario de la base de datos.

## Opción 1: db-dump (**ece-tools; recomendado**)

Puede volcar la base de datos utilizando [ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) comando:

```php
vendor/bin/ece-tools db-dump
```

Esta es la opción recomendada y más segura.

Consulte [Volcar la base de datos (ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) en nuestra Guía de infraestructura en la nube de Commerce.

## Opción 2: mysqldump

>[!WARNING]
>
>No ejecute este comando en el clúster de base de datos. El clúster no diferenciará si se ejecuta con la base de datos principal o con una secundaria. Si el clúster ejecuta este comando en el principal, la base de datos no podrá ejecutar escrituras hasta que se complete el volcado y esto podría afectar al rendimiento y a la estabilidad del sitio.

Puede volcar su base de datos utilizando el MySQL nativo `mysqldump` comando.

Todo el comando puede tener el siguiente aspecto:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

La copia de seguridad de la base de datos creada ejecutando `mysqldump` comando y guardado en `\tmp`, debe moverse de esta ubicación. No debe ocupar espacio de almacenamiento en `\tmp` (lo que podría causar problemas).

Para obtener las credenciales de la base de datos (host, nombre de usuario y contraseña), puede llamar al `MAGENTO_CLOUD_RELATIONSHIPS` variable de entorno:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Documentación relacionada:**

* [mysqldump: Un programa de backup de bases de datos](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) en la documentación oficial de MySQL.
* [Variables específicas de la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (consulte `MAGENTO_CLOUD_RELATIONSHIPS`) en nuestra Guía de infraestructura en la nube de Commerce.
