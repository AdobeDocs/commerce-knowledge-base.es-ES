---
title: Restaurar una instantánea de base de datos desde Ensayo o Producción
description: Este artículo muestra cómo restaurar una instantánea de la base de datos desde Ensayo o Producción en Adobe Commerce en la infraestructura en la nube.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: 193b5118342f380cef925766c0f7956a6592800c
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Restaurar una instantánea de base de datos desde [!DNL Staging] o [!DNL Production]

Este artículo muestra cómo restaurar una base de datos [!DNL snapshot] desde [!DNL Staging] o [!DNL Production] en la infraestructura de Adobe Commerce en Cloud Pro.


>[!NOTE]
>
>Estos métodos restaurarán la **instantánea completa**.
>&#x200B;>Si necesita restaurar la instantánea **parcialmente** (por ejemplo, restaurando únicamente las tablas de catálogo y dejando las tablas de pedidos intactas), debe consultar con su desarrollador o DBA.


## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Elija el más apropiado para su caso:

* [Método 1: transfiera la base de datos [!DNL dump] a su equipo local e impórtela](#meth2).
* [Método 2: importe la base de datos [!DNL dump] directamente desde el servidor](#meth3).

## Método 1: transferir la base de datos [!DNL dump] al equipo local e importarla {#meth2}


>[!NOTE]
>
> El formato de la instantánea de **proyectos de Azure** será diferente y contiene otras bases de datos que **no se pueden importar**.\
> Antes de importar la instantánea, debe realizar pasos adicionales para **extraer la base de datos apropiada** antes de continuar con la importación de volcado.

Estos son los pasos:

1. Usando [!DNL SFTP], vaya a la ubicación donde se ha colocado la base de datos [!DNL snapshot], normalmente en el primer servidor/nodo de su [!DNL cluster] (por ejemplo: `/mnt/recovery-<recovery_id>`).
   > **Proyectos basados en Azure:**\
   > Si el proyecto está basado en Azure (es decir, la dirección URL del proyecto es `https://us-a1.magento.cloud/projects/<cluster_id>`), la instantánea se colocará en:
   > * `/mnt/shared/<cluster ID>/all-databases.sql.gz`
   > * `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz`

   **Pasos de extracción específicos de Azure**

   **Para producción:**

   ```bash
   cd /mnt/shared/<cluster ID>/
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

   **Para ensayo:**

   ```bash
   cd /mnt/shared/<cluster ID_stg>/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `<cluster ID_stg>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Copie la base de datos [!DNL dump file] (por ejemplo: `<cluster ID>.sql.gz` para [!DNL Production] o `<cluster ID_stg>.sql.gz` para [!DNL Staging]) en el equipo local.
1. Asegúrese de haber configurado [!DNL SSH tunnel] para que se conecte de forma remota a la base de datos: [[!DNL SSH] y [!DNL sFTP]: [!DNL SSH tunneling]](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/secure-connections#env-start-tunn) en nuestra documentación para desarrolladores.
1. Conéctese a la base de datos.

   ```bash
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la base de datos; en el símbolo del sistema [!DNL MariaDB], escriba:

   (Para [!DNL Production])

   ```bash
   drop database <cluster ID>;
   ```

   (Para [!DNL Staging])

   ```bash
   drop database <cluster ID_stg>;
   ```

1. Escriba el siguiente comando para importar [!DNL snapshot]:

   (Para [!DNL Production])

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Para [!DNL Staging])

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Método 2: importar la base de datos [!DNL dump] directamente desde el servidor {#meth3}

Estos son los pasos:

1. Vaya a la ubicación en la que se ha colocado la base de datos [!DNL snapshot], normalmente en el primer servidor o nodo de su [!DNL cluster] (por ejemplo: `/mnt/recovery-<recovery_id>`).
1. Para [!DNL drop] y volver a crear la base de datos en la nube, conéctese primero a la base de datos:

   ```bash
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la base de datos; en el símbolo del sistema [!DNL MariaDB], escriba:

   (Para [!DNL Production])

   ```bash
   drop database <cluster ID>;
   ```

   (Para [!DNL Staging])

   ```bash
   drop database <cluster ID_stg>;
   ```

1. Después de borrar la base de datos, vuelva a crearla:

   ```bash
   create database [database_name];
   ```

1. Escriba el siguiente comando para importar [!DNL snapshot]:

   (Para importar la copia de seguridad de la base de datos desde [!DNL Production])

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Para importar la copia de seguridad de la base de datos desde [!DNL Staging])

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Para importar una copia de seguridad de base de datos desde cualquier otro entorno)

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Para importar una copia de seguridad de base de datos desde cualquier otro entorno)

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [Importar código: importe la base de datos](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)
* [[!DNL Snapshots] y [!DNL backup] administración: [!DNL Dump] su base de datos](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Copia de seguridad (instantánea) en la nube: FAQ](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/faq/backup-snapshot-on-cloud-faq)
