---
title: Restaurar una instantánea de base de datos desde Ensayo o Producción
description: Este artículo muestra cómo restaurar una instantánea de la base de datos desde Ensayo o Producción en Adobe Commerce en la infraestructura en la nube.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: ad0ec2e6dc1d3e1023ad4ecda595b5c942716407
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Restaurar una instantánea de base de datos desde [!DNL Staging] o [!DNL Production]

Este artículo muestra cómo restaurar una BD [!DNL snapshot] de [!DNL Staging] o [!DNL Production] en la infraestructura de Adobe Commerce en Cloud Pro.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Elija el más apropiado para su caso:

* [Método 1: transferencia de la base de datos [!DNL dump] a su equipo local e impórtelo](#meth2).
* [Método 2: importar la base de datos [!DNL dump] directamente desde el servidor](#meth3).

## Método 1: transferencia de la base de datos [!DNL dump] a su equipo local e impórtelo {#meth2}

Estos son los pasos:

1. Uso de [!DNL sFTP], vaya a la ubicación donde se encuentra la base de datos [!DNL snapshot] se ha colocado, normalmente en el primer servidor/nodo de su [!DNL cluster] (Por ejemplo: `/mnt/recovery-<recovery_id>`). NOTA: Si el proyecto se basa en Azure, es decir, la dirección URL del proyecto es similar a https://us-a1.magento.cloud/projects/&lt;cluster_id>, la instantánea se colocará en `/mnt/shared/<cluster ID>/all-databases.sql.gz` o `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` en su lugar.

   NOTA: El formato de la instantánea de los proyectos de Azure será diferente y contendrá otras bases de datos que no se pueden importar. Antes de importar la instantánea, deberá realizar pasos adicionales para extraer la base de datos adecuada antes de importar el volcado.

   Para la producción:

   ```sql
   cd /mnt/shared/<cluster ID/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   Para Ensayo:

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Copiar la base de datos [!DNL dump file] (Por ejemplo: `<cluster ID>.sql.gz` para [!DNL Production] o `<cluster ID_stg>.sql.gz` para [!DNL Staging]) al equipo local.
1. Asegúrese de haber configurado el [!DNL SSH tunnel] para conectarse a la base de datos de forma remota: [[!DNL SSH] y [!DNL sFTP]: [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) en nuestra documentación para desarrolladores.
1. Conéctese a la base de datos.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la base de datos; en el [!DNL MariaDB] , introduzca:

   (Para [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Para [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Introduzca el siguiente comando para importar el [!DNL snapshot]:

   (Para [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Para [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Método 2: importar la base de datos [!DNL dump] directamente desde el servidor {#meth3}

Estos son los pasos:

1. Vaya a la ubicación de la base de datos [!DNL snapshot] se ha colocado, normalmente en el primer servidor/nodo de su [!DNL cluster] (Por ejemplo: `/mnt/recovery-<recovery_id>`).
1. Hasta [!DNL drop] y vuelva a crear la base de datos en la nube, conéctese primero a la base de datos:

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la base de datos; en el [!DNL MariaDB] , introduzca:

   (Para [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Para [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Introduzca el siguiente comando para importar el [!DNL snapshot]:

   (Para importar la copia de seguridad de la base de datos desde [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Para importar la copia de seguridad de la base de datos desde [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Para importar una copia de seguridad de base de datos desde cualquier otro entorno)

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [Importar código: importe la base de datos](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots] y [!DNL backup] administración: [!DNL Dump] su base de datos](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
