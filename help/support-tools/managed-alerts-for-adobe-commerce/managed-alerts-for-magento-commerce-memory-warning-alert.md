---
title: "Alertas administradas para Adobe Commerce: alerta de advertencia de memoria"
description: Este artículo proporciona pasos de solución de problemas para cuando recibe una alerta de advertencia de memoria para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.
exl-id: bb5eb3f4-b162-4737-93d5-4037f2844bb1
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Alertas administradas para Adobe Commerce: alerta de advertencia de memoria

Este artículo proporciona pasos de solución de problemas para cuando recibe una alerta de advertencia de memoria para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![advertencia de memoria](assets/memory-warning-magento-managed.png){width="500"}

## Productos y versiones afectados

Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube

## Problema

Recibirá una alerta en New Relic si se ha registrado en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por Adobe Commerce para ofrecer a los clientes un conjunto estándar con información de Soporte e Ingeniería.

<u>**Hacer!**</u>:

* Se recomienda cancelar cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) en nuestra documentación para desarrolladores.

<u>**¡No!**</u>:

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales, lo que puede causar una tensión adicional en la CPU o el disco.
* Realice cualquier tarea administrativa importante (es decir, el administrador, las importaciones/exportaciones de datos).
* Borre la caché.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

1. Utilice la [página Infraestructura de APM de New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar los principales procesos que requieren mucha memoria. Para ver los pasos, consulte la [página Hosts de supervisión de infraestructura de New Relic > pestaña Procesos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Si servicios como Redis o MySQL son la principal fuente de consumo de memoria, pruebe lo siguiente:

   * Compruebe que está en la versión más reciente. Las versiones más recientes a veces pueden corregir las fugas de memoria. Si no dispone de la versión más reciente, considere la posibilidad de actualizar. Para ver los pasos, consulte [Adobe Commerce en la infraestructura de la nube > Servicios > Cambiar servicios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) en nuestra documentación para desarrolladores.
   * Si sigue sin poder identificar el origen del aumento del consumo de memoria, compruebe problemas de MySQL como consultas de larga ejecución, claves principales no definidas e índices duplicados. Para ver los pasos, consulte [Problemas más comunes de la base de datos en Adobe Commerce sobre la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) en nuestra base de conocimiento de asistencia.
   * Si no hay problemas con MySQL, compruebe si hay problemas con PHP. Revise los procesos en ejecución ejecutando `ps aufx` en CLI/Terminal. En la salida del terminal, verá los trabajos y procesos cron que se están ejecutando actualmente. Compruebe el resultado para el tiempo de ejecución de los procesos. Si hay un cron con un tiempo de ejecución largo, el cron puede estar colgando. Consulte [Rendimiento lento, crones lentos y de larga ejecución](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) y [Trabajo de cron atascado en estado de &quot;ejecución&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) en nuestra base de conocimiento de soporte para ver los pasos de solución de problemas.

1. Si sigue teniendo problemas para identificar el origen del problema, use la [página de transacciones de New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transacciones con problemas de rendimiento:

   * Ordene las transacciones según las puntuaciones de Apdex ascendentes. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hace referencia a la satisfacción del usuario con el tiempo de respuesta de sus aplicaciones y servicios web. Una [puntuación Apdex baja](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) puede indicar un cuello de botella (una transacción con un tiempo de respuesta más alto). Por lo general, es la base de datos, Redis o PHP. New Relic Para ver los pasos, consulte [Ver transacciones con mayor insatisfacción con Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordene las transacciones por el mayor rendimiento, el tiempo de respuesta medio más lento, el tiempo más lento y otros umbrales. Para ver los pasos, consulte New Relic [Buscar problemas de rendimiento específicos](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Si sigue teniendo problemas para identificar el problema, utilice la página Infraestructura de APM de New Relic.

1. Si no puede identificar la causa del aumento del consumo de memoria, revise las tendencias recientes para identificar los problemas con las implementaciones de código o los cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y grandes cambios en el catálogo). Se recomienda revisar los últimos siete días de actividad para cualquier correlación en implementaciones o cambios de código.

1. Si los métodos anteriores no le ayudan a encontrar la causa y/o la solución en un tiempo razonable, solicite un aumento o coloque el sitio en modo de mantenimiento si aún no lo ha hecho. Para ver los pasos, consulte [Cómo solicitar el cambio de tamaño temporal](/help/how-to/general/how-to-request-temporary-magento-upsize.md) en nuestra base de conocimiento de soporte técnico y [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores.

1. Si el cambio de tamaño devuelve el sitio a las operaciones normales, considere la posibilidad de solicitar un cambio de tamaño permanente (póngase en contacto con el equipo de cuenta de Adobe) o intente reproducir el problema en el ensayo dedicado ejecutando una prueba de carga y optimizando las consultas, o código que reduzca la presión sobre los servicios. Consulte [Adobe Commerce en la infraestructura de la nube > Implementación de pruebas > Pruebas de carga y esfuerzo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) en nuestra documentación para desarrolladores.
