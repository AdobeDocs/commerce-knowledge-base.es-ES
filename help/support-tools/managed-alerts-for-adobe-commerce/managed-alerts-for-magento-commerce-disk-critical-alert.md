---
title: "Alertas administradas para Adobe Commerce: alerta crítica de disco"
description: Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de disco crítica para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.
exl-id: 03e5694b-7689-4fbf-8781-636fa46ca0d3
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Alertas administradas para Adobe Commerce: alerta de disco crítico

Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de disco crítica para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![alerta crítica de disco](assets/disk-critical-magento-managed.png){width="500"}

## Productos y versiones afectados

Infraestructura en la nube de Adobe Commerce en arquitectura de plan Pro

## Problema

Recibirá una alerta en New Relic si se ha registrado en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas se desarrollaron por Adobe para ofrecer a los clientes un conjunto estándar con las perspectivas de Soporte e Ingeniería.

<u> **Hacer!** </u>

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) . Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt).

**¡No!**

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales que puedan causar estrés adicional en la CPU o el disco.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché.

Es posible que el sitio no responda (si aún no está experimentando una interrupción del sitio) si realiza alguna de las acciones &quot;No&quot; antes de haber investigado y resuelto la causa de la alerta.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

>[!WARNING]
>
>Como se trata de una alerta crítica, se recomienda completar el **Paso 1** antes de intentar solucionar el problema (Paso 2 en adelante).

1. Compruebe si existe un ticket de asistencia de Adobe Commerce. Para ver los pasos, consulte [Rastrear los tickets de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) en nuestra base de conocimiento de soporte. Es posible que el equipo de asistencia haya recibido una alerta de umbral de New Relic, haya creado un ticket y haya empezado a trabajar en el problema. Si no existe ningún ticket, cree uno. El ticket debe tener la siguiente información:
   * Motivo del contacto: seleccione &quot;Alerta CRÍTICA de New Relic recibida&quot;.
   * Descripción de la alerta.
   * [Vínculo a incidente de New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Esto se incluye en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. En New Relic, revise los discos para obtener el máximo uso. Para ver los pasos, consulte la ficha Almacenamiento en la página Hosts de supervisión de infraestructura de New Relic [: ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)
   * Si en New Relic observa un aumento lento en el uso del disco, pruebe las siguientes opciones:
   * Optimización del espacio en disco mediante el ajuste de la asignación de espacio. Para ver los pasos, consulte [Administrar espacio en disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) en nuestra documentación para desarrolladores. También es posible que necesite solicitar más espacio en disco (póngase en contacto con el equipo de cuenta de Adobe).
   * Borrar espacio en disco para MySQL. Consulte [El espacio en disco de MySQL es bajo](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) en nuestra base de conocimiento de soporte técnico para ver los pasos.
   * Si New Relic muestra un uso de disco que aumenta rápidamente, esto podría indicar que hay un problema que ha provocado que un archivo aumente muy rápidamente en un directorio. Realice las siguientes comprobaciones:
1. Compruebe el espacio en disco general para identificar el problema ejecutando el siguiente comando en CLI/Terminal: `df -h`
1. Después de identificar un directorio con un uso de disco inesperadamente grande y creciente, debe comprobar el sistema de archivos afectado. El ejemplo siguiente muestra cómo comprobar el directorio de archivos `pub/media/`. Este es el directorio que utiliza Commerce para almacenar registros y archivos multimedia grandes. Sin embargo, debe ejecutar este comando para cualquier directorio que muestre un uso de disco inesperado: `du -sch ~/pub/media/*`

Si la salida del terminal muestra un archivo en uno de estos directorios aumentando rápidamente el uso del disco y sabe que el contenido del archivo no es necesario, considere la posibilidad de quitar el archivo. Si no se siente cómodo al realizar esta acción, [envíe un ticket de soporte de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
