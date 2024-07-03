---
title: Actualice MariaDB 10.4 a 10.5 para Adobe Commerce en la nube
description: MariaDB 10.4 llega al final del soporte el 18 de junio de 2024. Este artículo explica cómo actualizar MariaDB de 10.4 a 10.5 para seguir utilizando Adobe Commerce en la infraestructura en la nube.
feature: Best Practices, Cloud
exl-id: 065840b8-28c1-4686-95fc-df3e73152845
source-git-commit: 11f2fae3264a61413c5da1b93ef4980151a1df1e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Actualice MariaDB 10.4 a 10.5 para Adobe Commerce en la nube

MariaDB es una base de datos de código abierto empresarial que se utiliza con Adobe Commerce.

MariaDB 10.4 llega al final del soporte en [18 de junio de 2024](https://endoflife.date/mariadb). Ya no es compatible con PCI cuando se encuentra en una versión no compatible de MariaDB. Este artículo explica cómo actualizar de MariaDB 10.4 a 10.5 para seguir utilizando Adobe Commerce en la infraestructura en la nube.

>[!NOTE]
>
>A medida que MariaDB 10.4 llega al final de su vida útil (EOL), ya no será compatible con las versiones actuales de Adobe Commerce. Lo más recomendable es dejar de usar cualquier versión EOL dentro de los 30 días posteriores a su EOL.

## Producto y versiones afectados

* Todas las infraestructuras locales y en la nube de Adobe Commerce 2.4.4 y 2.4.5

## Solución

Adopte los nuevos parches solo de seguridad (2.4.4-p9 o 2.4.5-p8) que se lanzarán el 11 de junio de 2024 para garantizar la compatibilidad con MariaDB 10.5. A continuación, siga los pasos para actualizar de MariaDB 10.4 a 10.5.

### Pasos de actualización para implementaciones en la nube

1. Crear un [Copia de seguridad de BD mediante comandos ECE-Tools DB backup](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Esta copia de seguridad debe realizarse antes de los pasos 2 y 3 en caso de que algo salga mal al actualizar tablas/filas.
1. [Comprobar y convertir todas las tablas compactas en tablas dinámicas](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). Este paso es necesario para evitar una posible pérdida de datos durante la actualización de la base de datos.
1. Compruebe si hay tablas MYISAM. Tienes que hacerlo [convertir todas las tablas MyISAM a InnoD](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. Después de preparar las tablas y filas de la base de datos (los dos pasos anteriores), cree un [Copia de seguridad de BD mediante comandos ECE-Tools DB backup](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Abra una solicitud de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para programar la actualización de MariaDB 10.4 a 10.5. En el ticket, indique la fecha y la hora en que desea actualizar la base de datos. El equipo de asistencia necesita un aviso de 48 horas, y el equipo de desarrollo del comerciante debe estar disponible. Una vez que se acuerden la hora y la fecha de la actualización, haga lo siguiente:
   1. Ponga su sitio en modo de mantenimiento y detenga cualquier actividad de base de datos, por ejemplo, crons.
   1. Crear un [Copia de seguridad de BD mediante comandos ECE-Tools DB backup](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Informe al servicio de asistencia de que ha completado la copia de seguridad mediante su vale de soporte. Para obtener los pasos para ver y rastrear sus tickets, consulte [Guía del usuario del Centro de ayuda de Adobe Commerce: Seguimiento de tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) en nuestra base de conocimiento de soporte.
   1. El equipo de asistencia de Adobe Commerce comienza el proceso de actualización de MariaDB. Si se han realizado todos los pasos anteriores y la base de datos tiene un tamaño promedio, el proceso tarda aproximadamente una hora. Los BD más grandes tardan más. Una vez completada la actualización, se le informará a través de su ticket.
1. Desactive el modo de mantenimiento. Consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores.

>[!NOTE]
>
>Se recomienda crear una copia de seguridad de la base de datos antes y después de cada paso de actualización para eliminar cualquier posibilidad de pérdida de datos. Esto le permitirá revertir a un paso anterior si surgen problemas en cualquier momento durante la actualización de la versión.

## Lectura relacionada

* [Guía de prácticas recomendadas de actualización de DB](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites) para implementaciones locales.
* [Actualice MariaDB 10.0 a 10.2 para Adobe Commerce en la nube](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) en nuestra base de conocimiento de soporte.
* [directiva de ciclo vital de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) en nuestra documentación para desarrolladores.
