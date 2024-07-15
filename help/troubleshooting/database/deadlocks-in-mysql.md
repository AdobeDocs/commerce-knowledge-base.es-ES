---
title: Interbloqueos en MySQL
description: Este artículo habla sobre los interbloqueos en MySQL para ayudar a identificarlos y resolverlos si causan un bloqueo del sitio, una importación atascada de la base de datos u otros problemas de Adobe Commerce.
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Interbloqueos en MySQL

Este artículo habla sobre los interbloqueos en MySQL para ayudar a identificarlos y resolverlos si causan un bloqueo del sitio, una importación atascada de la base de datos u otros problemas de Adobe Commerce.

## Productos y versiones afectados

* Adobe Commerce local 2.2.x y 2.3.x
* Adobe Commerce en la infraestructura en la nube 2.2.x y 2.3.x

## Problema

Los interbloqueos en MySQL se producen cuando dos o más transacciones se retienen mutuamente y solicitan bloqueos. Los interbloqueos que están presentes no siempre indican un problema, pero a menudo son un síntoma de algún otro problema de MySQL o Adobe Commerce que se ha producido.

A menudo, los registros de aplicación, implementación o MySQL mencionarán un error *&quot;interbloqueo&quot;* o el error *&quot;Interbloqueo encontrado al intentar obtener el bloqueo; intente reiniciar la transacción.&quot;*

## Causa

Los interbloqueos pueden tener varias causas, pero la más común es si realiza cualquier interacción (sitios web/procesos/trabajos cron/otros usuarios/mantenimiento de MySQL/importaciones de MySQL) mientras realiza consultas DML/DDL al mismo tiempo.

Por ejemplo, se recomienda evitar una importación atascada de la base de datos MySQL poniendo primero el sitio en modo de mantenimiento para evitar que las solicitudes SQL lleguen a la base de datos, lo que podría provocar interbloqueos y una importación atascada de la base de datos.

## Solución

1. Compruebe los registros de aplicación, implementación o MySQL para ver si hay errores de interbloqueo:
   * [Ubicaciones de registro de Magento Open Source y Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * [Adobe Commerce en la nube registra ubicaciones](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. Compruebe la lista de procesos MySQL para ejecutar procesos con el comando `mysql -e 'show full processlist';`
1. Si está en Adobe Commerce en una infraestructura en la nube, compruebe que el esclavo MySQL esté habilitado. Consulte este artículo: [Implementar variables (MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection).
1. En función de los errores involucrados, la solución puede presentarse por sí misma, o puede que necesite incluir su información de registro útil si necesita abrir un [ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lectura relacionada

* [Cómo minimizar y gestionar interbloqueos](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [Optimización del indizador: cambio de tabla del indizador](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [Operaciones en lotes - Consumir mensajes](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>Somos conscientes de que este artículo aún puede contener términos de software estándar en la industria que algunos pueden encontrar racistas, sexistas u opresivos y que pueden hacer que el lector se sienta herido, traumatizado o no deseado. El Adobe de está trabajando para eliminar estos términos de nuestro código, documentación y experiencias de usuario.
