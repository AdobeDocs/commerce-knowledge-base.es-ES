---
title: "Alertas administradas para Adobe Commerce: alerta de advertencia de disco"
description: Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de disco de advertencia para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.
exl-id: 07b34db1-11ec-4cf2-ae47-cfc067f91383
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Alertas administradas para Adobe Commerce: alerta de advertencia de disco

Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de disco de advertencia para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![alerta de advertencia de disco](assets/disk-warning-magento-managed.png){width="500"}

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, arquitectura de plan Pro.

## Problema

Recibirá una alerta en New Relic si se ha registrado en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas se desarrollaron por Adobe para ofrecer a los clientes un conjunto estándar con las perspectivas de Soporte e Ingeniería.

<u> **Hacer!** </u>

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) en nuestra documentación para desarrolladores.

<u> **¡No!** </u>

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales que puedan causar estrés adicional en la CPU o el disco.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché. Es posible que el sitio no responda (si aún no está experimentando una interrupción del sitio) si realiza alguna de las acciones &quot;No&quot; antes de haber investigado y resuelto la causa de la alerta.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa:

1. En New Relic, revise los discos para obtener el máximo uso. Para ver los pasos, consulte la ficha Almacenamiento en la página Hosts de supervisión de infraestructura de New Relic [1:](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)
   * Si en New Relic observa un aumento lento en el uso del disco, pruebe las siguientes opciones:
   * Optimización del espacio en disco mediante el ajuste de la asignación de espacio. Para ver los pasos, consulte [Administrar espacio en disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) en nuestra documentación para desarrolladores. También es posible que necesite solicitar más espacio en disco (póngase en contacto con el equipo de cuenta de Adobe).
   * Borrar espacio en disco para MySQL. Consulte [El espacio en disco de MySQL es bajo](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) para ver los pasos.
   * Si New Relic muestra un uso de disco que aumenta rápidamente, esto podría indicar que hay un problema que ha provocado que un archivo aumente muy rápidamente en un directorio. Realice las siguientes comprobaciones:
1. Compruebe el espacio en disco general para identificar el problema ejecutando el siguiente comando en CLI/Terminal: `df -h`
1. Después de identificar un directorio con un uso de disco inesperadamente grande y creciente, debe comprobar el sistema de archivos afectado. El ejemplo siguiente muestra cómo comprobar el directorio de archivos `pub/media/`. Este es el directorio que utiliza Adobe Commerce para almacenar registros y archivos multimedia grandes. Sin embargo, debe ejecutar este comando para cualquier directorio que muestre un uso de disco inesperado: `du -sch ~/pub/media/*`.

Si la salida del terminal muestra un archivo en uno de estos directorios aumentando rápidamente el uso del disco y sabe que el contenido del archivo no es necesario, considere la posibilidad de quitar el archivo. Si no se siente cómodo al realizar esta acción, [envíe un ticket de soporte de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
