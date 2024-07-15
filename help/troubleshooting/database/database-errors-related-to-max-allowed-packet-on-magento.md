---
title: Errores de base de datos relacionados con max_allowed_packet en Adobe Commerce
description: Este artículo proporciona una solución para los errores de conexión de base de datos en el var/log/exception.log que pueden producirse al importar un gran número de productos o al realizar otra tarea que obligue al servidor a gestionar paquetes más grandes que los establecidos en max_allowed_packet, que es más grande que el valor predeterminado de 16 MB.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Errores de base de datos relacionados con max_allowed_packet en Adobe Commerce

Este artículo proporciona una solución para los errores de conexión a la base de datos en `var/log/exception.log` que pueden producirse al importar un gran número de productos o al realizar otra tarea que obligue al servidor a gestionar paquetes mayores que los establecidos en `max_allowed_packet` que sean mayores que los 16 MB predeterminados.

## Productos y versiones afectados

* Adobe Commerce local, todas [las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Cuando un cliente MySQL o el servidor [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) recibe un paquete mayor de [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) bytes, emite un error de [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) (que se puede ver en `exception.log`) y cierra la conexión. Con algunos clientes, también puede que se produzca un error de *pérdida de conexión con el servidor MySQL durante query* si el paquete de comunicación es demasiado grande.

<u>Pasos a seguir</u>

Hay diversas tareas que pueden producir este problema. Esto puede incluir intentar importar un gran número de productos en Adobe Commerce o consultas transaccionales que devuelvan demasiados datos. El resultado son errores de conexión a la base de datos en `var/log/exception.log` y otros problemas, como que los productos no se importaron correctamente.

## Causa

El valor predeterminado de 16 MB para la configuración de MySQL `max_allowed_packets` no es lo suficientemente grande como para satisfacer sus necesidades.

## Solución

1. Identifique consultas en las que las filas individuales superen el límite actual de `max_allowed_packet`. Estas consultas deben reescribirse para reducir la cantidad de datos que se devuelven. Esto se puede hacer si se tiene un número menor de columnas en la instrucción `SELECT` o si se elige un tipo de datos más pequeño para varias columnas como parte del diseño de tabla. Si tiene una cuenta de New Relic, use la [página Errores de APM de New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) y la [página Bases de datos de APM de New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time), y [Registros de New Relic](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) para buscar las consultas relevantes.
1. Para una corrección rápida, puede solicitar temporalmente que el tamaño de `max_allowed_packet` aumente cuando [envíe un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), pero esto depende del equipo de ingeniería de clientes, ya que un valor demasiado grande puede provocar errores de replicación al causar congestión de red.
1. Como práctica recomendada, debe ejecutar el siguiente comando en la CLI para algunas de las tablas de base de datos grandes:

   ```
   show table status like [table name to match]
   ```

   Evalúe las consultas que se ejecutan en estas tablas para determinar si se sobrepasa el tamaño recomendado de `max_allowed_packet` de 16 MB. Siga el mismo proceso en el paso uno para reducir los datos que devuelven estas consultas.

## Lectura relacionada

* [Guía de instalación > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) en nuestra documentación para desarrolladores.
* [La carga de la base de datos pierde la conexión con MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) en nuestra base de conocimiento de soporte.
* [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) en nuestra base de conocimiento de soporte.
* [Prácticas recomendadas para resolver problemas de rendimiento de la base de datos](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) en nuestra base de conocimiento de soporte.
