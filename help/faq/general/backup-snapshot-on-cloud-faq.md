---
title: 'Copia de seguridad (instantánea) en la nube: preguntas frecuentes'
description: Este artículo cubre los aspectos básicos del backup de sus entornos con instantáneas en Adobe Commerce en la infraestructura en la nube.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 9e218e3fadbf9941c94d309fcfb6f258d2f4faf2
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# Copia de seguridad (instantánea) en la nube: preguntas frecuentes

Este artículo cubre la realización de copias de seguridad de sus entornos con instantáneas en Adobe Commerce en la infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube 2.4.x
* Planos de arquitectura: Starter, Pro Legacy, Pro

## Instantánea de entorno, plan Pro

### Entornos de ensayo y producción

* Las instantáneas manuales no están disponibles para los entornos de ensayo y producción en el plan Pro.
* Las instantáneas automáticas se crean **independientemente del estado activo** del sitio (las instantáneas también se crean para sitios que aún no se han iniciado). Las copias de seguridad automáticas no son de acceso público porque se almacenan en un sistema independiente.
Puedes [enviar un ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) para solicitar una copia de seguridad especial o para restaurar desde una copia de seguridad específica, proporcionando la fecha, la hora y la zona horaria del ticket. Una vez que el equipo de infraestructura haya proporcionado la instantánea, para determinar la marca de tiempo cuando se tomó originalmente, ejecute el siguiente comando desde la ubicación donde se colocó la instantánea:

  `cat /mnt/recovery/vol-<volume_id>/snap.time`

  Ejemplo de salida:

  <strong>2025-01-13 08:42:17.123000+00:00</strong>


* La compatibilidad no genera instantáneas manuales bajo demanda. Además, tenga en cuenta que la asistencia técnica no realiza la reversión ni la restauración de la base de datos por usted: recuperan la instantánea, pero debe restaurar la base de datos usted mismo.
* Las instantáneas automáticas se crean **independientemente del estado activo** del sitio (las instantáneas también se crean para sitios que aún no se han iniciado). Las copias de seguridad automáticas se almacenan en un sistema independiente y el público no puede acceder a ellas.
Puedes [enviar un ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) para solicitar una copia de seguridad especial o para restaurar desde una copia de seguridad específica, proporcionando la fecha, la hora y la zona horaria del ticket. La compatibilidad no genera instantáneas manuales bajo demanda.
Además, tenga en cuenta que la asistencia técnica no realiza la reversión ni la restauración de la base de datos por usted: recuperan la instantánea, pero debe restaurar la base de datos usted mismo.
* Las copias de seguridad se crean con las **instantáneas cifradas del Almacén de bloques elásticos de Amazon Web Service (AWS EBS)**.
* Las instantáneas de entorno incluyen el sistema completo (el sistema de archivos y la base de datos).
* El tiempo de retención de instantáneas automáticas **es diferente** y sigue [la programación](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery).

>[!NOTE]
>
>La consola de Cloud siempre muestra [!UICONTROL No backup] en los entornos de ensayo y producción. Solo puede realizar copias de seguridad desde el entorno de integración. Seleccione **[!UICONTROL Backup]** en el menú desplegable de los tres puntos.
>
>![cloud_console_backup.png](assets/cloud_console_backup.png)

### Entorno de integración (desarrollo)

* [No se está haciendo una copia de seguridad de su entorno de integración](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-27242) **de forma automática**, pero puede crear instantáneas **manualmente**.
* Puede crear instantáneas manuales para entornos de integración en tiendas que no estén activas.
* Es posible que tenga **varias instantáneas** que se hayan activado manualmente.
* Se almacena una instantánea desencadenada manualmente durante **7 días**.

**Artículos relacionados en nuestra documentación para desarrolladores:**

* [Copia de seguridad y recuperación ante desastres](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [Crear una instantánea](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/storage/snapshots)

## Instantánea de entorno, plan de inicio

* No se realiza automáticamente una copia de seguridad de todos los tipos de entornos (integración, ensayo, producción) **pero puede crear instantáneas manualmente.**
* Puede crear instantáneas manuales **independientemente del estado activo** del sitio (instantáneas también creadas para sitios que aún no se han iniciado).
* Se almacena una instantánea desencadenada manualmente durante **7 días**.

## Restaurar una instantánea de entorno

Para restaurar una instantánea existente (en el entorno admitido: integración, ensayo, producción en el plan inicial o integración en el plan Pro), siga los pasos de [Administración de copias de seguridad: restaure una copia de seguridad manual](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) en nuestra Guía de infraestructura de Commerce en la nube.

## Copia de seguridad de base de datos

La copia de seguridad de la base de datos forma parte de una instantánea de Cloud:

Una instantánea es una copia de seguridad completa de un entorno que incluye todos los datos persistentes de todos los servicios en ejecución (por ejemplo, **su base de datos MySQL**, Redis, etc.) y cualquier archivo almacenado en los volúmenes montados.

>[!NOTE]
>
>Los volúmenes montados solo incluyen los [montajes grabables](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/app/properties/properties#mounts), o hacen referencia a ellos, y no incluirán todo el directorio `/app`. En cuanto a los otros archivos, se crean o generan por [el proceso de compilación e implementación](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow), y también tendrá que retirar los archivos restantes de su repositorio Git.

[Administración de instantáneas y copias de seguridad](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/storage/snapshots) en nuestra documentación para desarrolladores.

Envíe solamente una [solicitud de soporte](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) para una instantánea de base de datos de Pro Production y Staging si necesita la base de datos de un momento específico. Si solo necesita una copia de seguridad actual de su base de datos (en cualquier entorno), consulte el artículo de la base de conocimiento: [Generar volcados de base de datos en la nube](/help/how-to/general/create-database-dump-on-cloud.md).
