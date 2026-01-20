---
title: Errores de base de datos relacionados con max_allowed_packet en Adobe Commerce
description: Este artículo proporciona una solución para los errores de conexión de base de datos en el var/log/exception.log que pueden producirse al importar un gran número de productos o al realizar otra tarea que obligue al servidor a gestionar paquetes más grandes que los establecidos en max_allowed_packet, que es más grande que el valor predeterminado de 16 MB.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Errores de base de datos relacionados con max_allowed_packet en Adobe Commerce

Este artículo proporciona una solución para los errores de conexión a la base de datos en `var/log/exception.log` que pueden producirse al importar un gran número de productos o al realizar otra tarea que obligue al servidor a gestionar paquetes mayores que los establecidos en `max_allowed_packet` que sean mayores que los 16 MB predeterminados.

## Productos y versiones afectados

* Adobe Commerce local, todas [las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Cuando un cliente de [!DNL MySQL] o el servidor [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) recibe un paquete con más de [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) bytes, emite un error de [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) (que se puede ver en `exception.log`) y cierra la conexión. Con algunos clientes, también puede sufrir un error de *pérdida de conexión con el servidor [!DNL MySQL] durante el error query* si el paquete de comunicación es demasiado grande.

<u>Pasos a seguir</u>

Hay diversas tareas que pueden producir este problema. Esto puede incluir intentar importar un gran número de productos en Adobe Commerce o consultas transaccionales que devuelvan demasiados datos. El resultado son errores de conexión a la base de datos en `var/log/exception.log` y otros problemas, como que los productos no se importaron correctamente.

## Causa

El valor predeterminado de 16 MB para la configuración de [!DNL MySQL] `max_allowed_packets` no es lo suficientemente grande como para satisfacer sus necesidades.

## Solución

1. Identifique consultas en las que las filas individuales superen el límite actual de `max_allowed_packet`. Estas consultas deben reescribirse para reducir la cantidad de datos que se devuelven. Esto se puede hacer si se tiene un número menor de columnas en la instrucción `SELECT` o si se elige un tipo de datos más pequeño para varias columnas como parte del diseño de tabla. Si tiene una cuenta de New Relic, use la [página Errores de APM de New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) y la [página Bases de datos de APM de New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time), y [Registros de New Relic](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) para buscar las consultas relevantes.
1. Para una corrección rápida, puede solicitar temporalmente que el tamaño de `max_allowed_packet` aumente cuando [envíe un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), pero esto depende del equipo de ingeniería de clientes, ya que un valor demasiado grande puede provocar errores de replicación al causar congestión de red.
1. Como práctica recomendada, debe ejecutar el siguiente comando en la CLI para algunas de las tablas de base de datos grandes:

   ```
   show table status like [table name to match]
   ```

   Evalúe las consultas que se ejecutan en estas tablas para determinar si se sobrepasa el tamaño recomendado de `max_allowed_packet` de 16 MB. Siga el mismo proceso en el paso uno para reducir los datos que devuelven estas consultas.

## Lectura relacionada

* [Descripción general de la instalación local](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/overview) en nuestra documentación para desarrolladores.
* [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=es) en nuestra base de conocimiento de soporte.
* [Prácticas recomendadas para resolver problemas de rendimiento de la base de datos](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=es) en nuestra base de conocimiento de soporte.
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
