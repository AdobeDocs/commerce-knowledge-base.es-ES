---
title: "Alertas administradas en Adobe Commerce: alerta crítica de memoria"
description: Este artículo proporciona pasos de solución de problemas cuando recibe una alerta crítica de memoria para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Alertas administradas en Adobe Commerce: alerta crítica de memoria

Este artículo proporciona pasos de solución de problemas cuando recibe una alerta crítica de memoria para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![alerta crítica de disco](assets/memory-critical-magento-managed.png){width="500"}

## Productos y versiones afectados

Todas las versiones de Adobe Commerce en la infraestructura en la nube planifican la arquitectura Pro.

## Problema

Recibirá una alerta administrada en New Relic si se ha registrado en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas se desarrollaron por Adobe para ofrecer a los clientes un conjunto estándar con las perspectivas de Soporte e Ingeniería.

<u> **Hacer!** </u>

* Anule cualquier implementación programada hasta que se borre esta alerta
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) en nuestra documentación para desarrolladores.

<u>**¡No!**</u>

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

1. Compruebe si existe un ticket de asistencia de Adobe Commerce. Para ver los pasos, consulta [Rastrear tus tickets de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) en nuestra base de conocimiento de soporte. Es posible que el equipo de asistencia ya haya recibido una alerta de umbral de New Relic, haya creado un ticket y haya empezado a trabajar en el problema. Si no existe ningún ticket, cree uno. El ticket debe tener la siguiente información:
   * Motivo del contacto: seleccione &quot;Alerta CRÍTICA de New Relic recibida&quot;
   * Descripción de la alerta
   * [Vínculo a incidente de New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Esto se incluye en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Utilice la [página Infraestructura de APM de New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar los procesos con mayor consumo de memoria. Para ver los pasos, consulte la [página Hosts de supervisión de infraestructura de New Relic > pestaña Procesos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Si servicios como Redis, MySQL o PHP son las principales fuentes de consumo de memoria, pruebe lo siguiente:
1. Compruebe que está en las versiones más recientes. Las versiones más recientes a veces pueden corregir las fugas de memoria. Si no dispone de la versión más reciente, considere la posibilidad de actualizar. Para ver los pasos, consulte [Adobe Commerce en la infraestructura de la nube > Servicios > Cambiar servicios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) en nuestra documentación para desarrolladores.
1. Si el problema con el servicio no está relacionado con la versión, intente lo siguiente:
1. **MySQL**: compruebe problemas como consultas de larga ejecución, claves principales no definidas e índices duplicados. Para ver los pasos, consulte [Problemas más comunes de la base de datos en Adobe Commerce sobre la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) en nuestra base de conocimiento de asistencia.
1. **Redis**: Si Redis es una de las principales fuentes de consumo de memoria, [envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
1. **PHP**: Si PHP es una fuente de consumo de memoria superior, revise los procesos en ejecución ejecutando `ps aufx` en CLI/Terminal. En la salida de terminal verá trabajos y procesos cron que se están ejecutando actualmente. Compruebe el resultado para el tiempo de ejecución de los procesos. Si hay un cron con un tiempo de ejecución largo, el cron puede estar colgando. Para ver los pasos de solución de problemas, consulte [Rendimiento lento, crones lentos y de larga ejecución](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) y [Trabajo de cron atascado en estado de &quot;ejecución&quot;](https://support.magento.com/hc/en-us/articles/360033099451) en nuestra base de conocimiento de asistencia.
1. Si sigue teniendo problemas para identificar el origen del problema, use la [página de transacciones de New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transacciones con problemas de rendimiento:
   * Ordene las transacciones según las puntuaciones de Apdex ascendentes. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hace referencia a la satisfacción del usuario con el tiempo de respuesta de sus aplicaciones y servicios web. Una [puntuación Apdex baja](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) puede indicar un cuello de botella (una transacción con un tiempo de respuesta más alto). Normalmente es la base de datos, Redis, o PHP. New Relic Para ver los pasos, consulte [Ver transacciones con mayor insatisfacción con Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordene las transacciones por el mayor rendimiento, el tiempo de respuesta medio más lento, el tiempo más lento y otros umbrales. Para ver los pasos, consulte New Relic [Buscar problemas de rendimiento específicos](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Si sigue teniendo problemas para identificar el problema, utilice la página Infraestructura de APM de New Relic.
1. Si no puede identificar la causa del aumento del consumo de memoria, revise las tendencias recientes para identificar los problemas con las implementaciones de código o los cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y grandes cambios en el catálogo). Se recomienda revisar los últimos 7 días de actividad para cualquier correlación en implementaciones o cambios de código.
1. Si los métodos anteriores no le ayudan a encontrar la causa y/o la solución en un tiempo razonable, solicite un aumento o coloque el sitio en modo de mantenimiento si aún no lo ha hecho. Para ver los pasos, consulte [Cómo solicitar el cambio de tamaño temporal](/help/how-to/general/how-to-request-temporary-magento-upsize.md) en nuestra base de conocimiento de soporte técnico y [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores.
1. Si el cambio de tamaño devuelve el sitio a las operaciones normales, considere la posibilidad de solicitar un cambio de tamaño permanente (póngase en contacto con el equipo de cuenta de Adobe) o intente reproducir el problema en el ensayo dedicado ejecutando una prueba de carga y optimizando las consultas, o código que reduzca la presión sobre los servicios. Consulte [Adobe Commerce en la infraestructura de la nube > Implementación de pruebas > Pruebas de carga y esfuerzo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) en nuestra documentación para desarrolladores.
