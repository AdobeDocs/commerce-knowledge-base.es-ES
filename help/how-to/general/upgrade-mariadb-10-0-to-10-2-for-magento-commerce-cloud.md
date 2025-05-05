---
title: Actualice MariaDB 10.0 a 10.2 para Adobe Commerce en la nube
description: MariaDB 10.0 y 10.1 son el final de su vida útil (EOL). [La asistencia finalizó el 31 de marzo de 2019 y el 17 de octubre de 2020, respectivamente](https://endoflife.date/mariadb). Este artículo explica cómo actualizar MariaDB de 10.0 a 10.2 o 10.2 a 10.3 o a 10.4, para utilizar Adobe Commerce en la infraestructura en la nube.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Actualice MariaDB 10.0 a 10.2 para Adobe Commerce en la nube

MariaDB 10.0 y 10.1 son el final de su vida útil (EOL). [La asistencia finalizó el 31 de marzo de 2019 y el 17 de octubre de 2020, respectivamente](https://endoflife.date/mariadb). Este artículo explica cómo actualizar MariaDB de 10.0 a 10.2 o 10.2 a 10.3 o a 10.4, para utilizar Adobe Commerce en la infraestructura en la nube.

>[!NOTE]
>
>MariaDB 10.0 es el final de su vida útil (EOL) y no es compatible con las versiones actuales de Adobe Commerce. Lo más recomendable es dejar de usar cualquier versión EOL dentro de los 30 días posteriores a su EOL.

## Producto y versiones afectados

* Se recomienda MariaDB 10.2 para Adobe Commerce en la infraestructura en la nube 2.3.x.
* Se recomienda MariaDB 10.4 para 2.4.x. MariaDB 10.3 también es compatible con Adobe Commerce en la infraestructura en la nube 2.4.x.

## Pasos de actualización

Para actualizar de MariaDB 10.0 a 10.2 o 10.2 a 10.3 o a 10.4, complete los siguientes pasos:

1. Crear una copia de seguridad de [DB mediante los comandos de copia de seguridad ECE-Tools DB](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Esto debe hacerse antes de los pasos 2 y 3 en caso de que algo salga mal al actualizar tablas/filas.
1. [Comprobar y convertir todas las tablas compactas en tablas dinámicas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=es). Esto es necesario para evitar la posible pérdida de datos durante la actualización de la base de datos.
1. Compruebe si hay tablas MYISAM. Debe [convertir todas las tablas MyISAM a InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=es).
1. Después de preparar las tablas y filas de la base de datos (los dos pasos anteriores), cree una copia de seguridad de [DB con los comandos ECE-Tools DB backup](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Abra un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para programar la actualización de MariaDB 10.0 a 10.2 o 10.2 a 10.3 o 10.4. En el ticket, especifique la fecha y la hora en que desea actualizar la base de datos. El equipo de asistencia necesita un aviso de 48 horas y el equipo de desarrollo de comerciantes debe estar disponible. Una vez que se acuerden la hora y la fecha de la actualización, haga lo siguiente:
   1. Ponga su sitio en modo de mantenimiento y detenga cualquier actividad de la base de datos, por ejemplo, crons.
   1. Crear una copia de seguridad de [DB mediante los comandos de copia de seguridad ECE-Tools DB](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Informe al equipo de asistencia de que ha completado la copia de seguridad. Haga esto a través de su ticket de asistencia. Para obtener los pasos para ver y rastrear tus tickets, consulta la [Guía del usuario del Centro de ayuda de Adobe Commerce: Rastrea tus tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) en nuestra base de conocimiento de asistencia.
   1. El equipo de asistencia de Adobe Commerce iniciará el proceso de actualización de MariaDB. Si se han realizado todos los pasos anteriores y la base de datos tiene un tamaño promedio, esto se puede hacer en aproximadamente una hora. Las bases de datos más grandes tardarán más. Se le informará a través de su ticket una vez que se haya completado la actualización.
1. Desactive el modo de mantenimiento. Consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre los requisitos de Adobe Commerce 2.4.x, consulte [Requisitos del sistema de Adobe Commerce 2.4 > Base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/system-requirements#database) en nuestra documentación para desarrolladores.
