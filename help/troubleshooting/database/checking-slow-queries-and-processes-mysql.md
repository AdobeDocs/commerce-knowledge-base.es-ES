---
title: Comprobación de consultas y procesos lentos en MySQL
description: Este artículo habla sobre un par de problemas comunes de MySQL (consultas lentas, procesos que tardan demasiado) que pueden afectar negativamente al sitio de un comerciante y las soluciones que indican.
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Comprobación de consultas y procesos lentos en MySQL

Este artículo habla sobre un par de problemas comunes de MySQL (consultas lentas, procesos que tardan demasiado) que pueden afectar negativamente al sitio de un comerciante y las soluciones que indican.

## Comprobando &quot;consultas lentas&quot; de MySQL

### Descripción

Si ha sufrido una interrupción que podría deberse a una base de datos sobrecargada, estos pasos le ayudarán a comprobar el registro de consultas lentas de la base de datos.

### Analizar consultas mediante la línea de comandos de MySQL (Adobe Commerce Cloud/local/Magento Open Source)

1. Inicie sesión en la línea de comandos de MySQL (Adobe Commerce local/Magento Open Source) o en el servidor en la nube desde la línea de comandos (Adobe Commerce en la infraestructura en la nube).
1. Examine el registro de consultas lentas en busca de consultas de más de 50 segundos:

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. Vaya a <https://www.unixtimestamp.com/> (o a un convertidor de marcas de tiempo Unix similar) e inserte la marca de tiempo del momento en que se ejecutó la consulta lenta.
1. Si el tiempo se correlaciona con cualquier interrupción del sitio que haya experimentado, podría deberse a una base de datos sobrecargada. Compruebe qué cargas había en la base de datos en ese momento. Algunos ejemplos de estas cargas podrían ser:

* Procesos Cron
* Tráfico (bots o personas)
* Importar/exportar scripts
* Creación de volcados


### Analizar consultas con [!DNL Percona Toolkit] (Adobe Commerce Pro: solo arquitectura de nube)

Si el proyecto de Adobe Commerce está implementado en una arquitectura Pro, puede usar [!DNL Percona Toolkit] para analizar consultas.

1. Ejecute el comando `pt-query-digest --type=slowlog` con los registros de consulta lentos de MySQL.
   * Para encontrar la ubicación de los registros de consultas lentas, consulte **[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)** en nuestra documentación para desarrolladores.
   * Consulte la documentación de [[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest).
1. En función de los problemas encontrados, realice pasos para corregir la consulta, de modo que se ejecute más rápidamente.

## Comprobando la &quot;lista de procesos&quot; de MySQL

### Descripción

Esto ayudará a identificar si el servidor MySQL está activo y si no hay consultas atascadas.

### Pasos

1. Inicie sesión en la línea de comandos de MySQL (Adobe Commerce local/Magento Open Source) o en el servidor en la nube desde la línea de comandos (Adobe Commerce en la infraestructura en la nube).
1. Inicie sesión en MySQL utilizando el bloque de código siguiente. Esto automatizará el proceso de inicio de sesión.

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. Si vuelve a recibir un error o tarda más de 30 segundos en responder, debe ponerse en contacto con el soporte técnico para comprobar el servidor MySQL.
1. Se está viendo el resultado de muestra.

1. A continuación se muestra un ejemplo de salida:

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. Compruebe la columna &quot;Tiempo&quot; para cualquier tiempo superior a 1800 segundos; esto indica un proceso que podría tardar demasiado tiempo en completarse. Observe el estado de los procesos en la columna &quot;Estado&quot;.
1. Revise las consultas y, posiblemente, mátelas si se descubre que no se espera que se ejecuten durante ese periodo de tiempo. Es posible que se esperen consultas de larga ejecución.


## Lectura relacionada

* [Sintaxis de MySQL Show Processlist](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) en dev.mysql.com.
* [Sintaxis de MySQL Kill](https://dev.mysql.com/doc/refman/8.0/en/kill.html) en dev.mysql.com.
* [Seguridad, rendimiento y administración de datos](https://developer.adobe.com/commerce/php/best-practices/extensions/security/) en nuestra documentación para desarrolladores.
* [Ayuda de MySQL](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql) en nuestra documentación para desarrolladores.
