---
title: "Alertas administradas para Adobe Commerce: Alerta de advertencia de Apdex"
description: Este artículo proporciona pasos para la resolución de problemas cuando recibe una alerta de advertencia Apdex para Adobe Commerce en New Relic. La puntuación Apdex mide la satisfacción de los usuarios con el tiempo de respuesta de las aplicaciones y servicios web. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.
exl-id: 6e3f28ae-734b-468f-b6a5-c4f2edb1cb4b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 3493214b468ac93dc938690495ea0a6bcf645a29
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Alertas administradas para Adobe Commerce: alerta de advertencia de Apdex

Este artículo proporciona pasos para la resolución de problemas cuando recibe una alerta de advertencia Apdex para Adobe Commerce en New Relic. La puntuación Apdex mide la satisfacción de los usuarios con el tiempo de respuesta de las aplicaciones y servicios web. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![alerta de advertencia de apdex](assets/apdex-warning-magento-managed.png){width="500"}

## Productos y versiones afectados

* Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube
* Adobe Commerce en infraestructura en la nube Arquitectura del plan inicial

## Problema

Recibirá una alerta administrada en New Relic si se ha registrado en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por el Adobe para ofrecer a los comerciantes un conjunto estándar utilizando perspectivas de Soporte e Ingeniería.

<u> **Hacer!** </u>

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) en nuestra documentación para desarrolladores. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) en nuestra documentación para desarrolladores.

<u>**¡No!**</u>

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales que puedan causar estrés adicional en la CPU o el disco.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

1. Para identificar el origen del problema, use la [página de transacciones de New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar las transacciones con problemas de rendimiento:
   * Ordene las transacciones según las puntuaciones de Apdex ascendentes. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hace referencia a la satisfacción del usuario con el tiempo de respuesta de sus aplicaciones y servicios web. Una [puntuación Apdex baja](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) puede indicar un cuello de botella (una transacción con un tiempo de respuesta más alto). Normalmente es la base de datos, Redis, o PHP. New Relic Para ver los pasos, consulte [Ver transacciones con mayor insatisfacción con Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordene las transacciones por el mayor rendimiento, el tiempo de respuesta medio más lento, el tiempo más lento y otros umbrales. Para ver los pasos, consulte New Relic [Buscar problemas de rendimiento específicos](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Utilice la [página Infraestructura de APM de New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar los procesos que requieren muchos recursos. Para ver los pasos, consulte la [página Hosts de supervisión de infraestructura de New Relic > pestaña Procesos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si servicios como Redis o MySQL son la principal fuente de consumo de memoria, pruebe lo siguiente:
   * Compruebe que está en la versión más reciente. Las versiones más recientes a veces pueden corregir las fugas de memoria. Si no dispone de la versión más reciente, considere la posibilidad de actualizar. Para ver los pasos, consulte [Cloud for Adobe Commerce > Servicios > Cambiar servicios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) en nuestra documentación para desarrolladores.
1. Si el problema no se debe a las versiones del servicio:
   * Compruebe otros problemas de MySQL, como consultas de larga ejecución, claves principales no definidas e índices duplicados. Para ver los pasos, consulte [Problemas más comunes de la base de datos en Adobe Commerce sobre la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) en nuestra base de conocimiento de asistencia.
   * Compruebe si hay otros problemas con PHP. Revise los procesos en ejecución ejecutando `ps aufx` en CLI/Terminal. En la salida de terminal verá trabajos y procesos cron que se están ejecutando actualmente. Compruebe el resultado para el tiempo de ejecución de los procesos. Si hay un cron con un tiempo de ejecución largo, el cron puede estar colgando. Para resolver problemas, consulte [Rendimiento lento, crones lentos y de larga ejecución](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) y [Trabajo de cron atascado en estado de &quot;ejecución&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) en nuestra base de conocimiento de soporte.
1. Una vez identificada una fuente potencial del problema, SSH en el entorno para investigar más a fondo. Para ver los pasos, consulte [Cloud for Adobe Commerce > Tecnologías y requisitos > SSH en su entorno](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) en nuestra documentación para desarrolladores.
1. Si sigue teniendo problemas para identificar el origen, revise las tendencias recientes para identificar problemas con implementaciones de código o cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y grandes cambios en el catálogo). Se recomienda revisar los últimos siete días de actividad para cualquier correlación en implementaciones o cambios de código.
1. Si no puede encontrar una solución en un plazo razonable, solicite un aumento o coloque un sitio en modo de mantenimiento si aún no lo ha hecho. Para ver los pasos, consulte [Cómo solicitar el cambio de tamaño temporal](/help/how-to/general/how-to-request-temporary-magento-upsize.md) en nuestra base de conocimiento de soporte técnico y [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) en nuestra documentación para desarrolladores.
1. Si [upsize](/help/how-to/general/how-to-request-temporary-magento-upsize.md) devuelve el sitio a operaciones normales, considere la posibilidad de solicitar un upsize permanente (póngase en contacto con el equipo de cuenta de Adobe) o intente reproducir el problema en su entorno de ensayo dedicado ejecutando una prueba de carga y optimizando las consultas, o código que reduzca la presión sobre los servicios. Consulte [Cloud for Adobe Commerce > Implementación de pruebas > Pruebas de carga y esfuerzo](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) en nuestra documentación para desarrolladores.
