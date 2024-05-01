---
title: "Alertas administradas para Adobe Commerce: alerta de advertencia de CPU"
description: Este artículo proporciona pasos de solución de problemas cuando recibe una alerta de advertencia de CPU para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Alertas administradas para Adobe Commerce: alerta de advertencia de CPU

Este artículo proporciona pasos de solución de problemas cuando recibe una alerta de advertencia de CPU para Adobe Commerce en New Relic. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![Alerta de advertencia de CPU](assets/cpu-warning-magento-managed.png){width="500"}

## Productos y versiones afectados

Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube

## Problema

Recibirá una alerta en New Relic si se ha registrado en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) y se han superado uno o más de los umbrales de alerta. Estas alertas se desarrollaron por Adobe para ofrecer a los clientes un conjunto estándar con las perspectivas de Soporte e Ingeniería.

<u> **¡Hazlo!** </u>

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde completamente. Para ver los pasos, consulte [Guía de instalación > Activar o desactivar el modo de mantenimiento](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) en nuestra documentación para desarrolladores. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) en nuestra documentación para desarrolladores.

<u>**¡No lo hagas!**</u>

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales que puedan causar estrés adicional en la CPU o el disco.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

1. Uso [Página de transacciones de APM de New Relic](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transacciones con problemas de rendimiento:
   * Ordene las transacciones según las puntuaciones de Apdex ascendentes. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hace referencia a la satisfacción del usuario con el tiempo de respuesta de sus aplicaciones y servicios web. [Una puntuación Apdex baja](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) puede indicar un cuello de botella (una transacción con un tiempo de respuesta más alto). Normalmente es la base de datos, Redis, o PHP. Para ver los pasos, consulte New Relic [Ver transacciones con mayor insatisfacción con Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordene las transacciones por el mayor rendimiento, el tiempo de respuesta medio más lento, el tiempo más lento y otros umbrales. Para ver los pasos, consulte New Relic [Buscar problemas de rendimiento específicos](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Si sigue teniendo problemas para identificar la fuente, utilice [Página de infraestructura de APM de New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar servicios con recursos pesados. Para ver los pasos, consulte New Relic [Monitorización de la infraestructura: página Hosts > pestaña Procesos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si identifica la fuente, SSH en el entorno para investigar más a fondo. Para ver los pasos, consulte [Cloud para Adobe Commerce > SSH en su entorno](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) en nuestra documentación para desarrolladores.
1. Si sigue teniendo problemas para identificar la fuente:
   * Revise las tendencias recientes para identificar los problemas con las implementaciones de código o los cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y grandes cambios en el catálogo). Se recomienda revisar los últimos siete días de actividad para cualquier correlación en implementaciones o cambios de código.
   * Considere la posibilidad de buscar y deshabilitar catálogos planos. Para ver los pasos, consulte [Lento rendimiento, crons lentos y de larga duración](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) en nuestra base de conocimiento de soporte.
   * Si sospecha que está experimentando un ataque DDoS, intente bloquear el tráfico de bots. Para ver los pasos, consulte [Cómo bloquear el tráfico malintencionado para Adobe Commerce en el nivel Rápido](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) en nuestra base de conocimiento de soporte.
1. Si el problema parece temporal, realice pasos de mitigación como un aumento de tamaño o ponga el sitio en modo de mantenimiento. Para ver los pasos, consulte [Cómo solicitar el cambio de tamaño temporal](/help/how-to/general/how-to-request-temporary-magento-upsize.md) en nuestra base de conocimiento de soporte, y [Guía de instalación > Activar o desactivar el modo de mantenimiento](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) en nuestra documentación para desarrolladores. Si el cambio de tamaño devuelve el sitio a las operaciones normales, considere la posibilidad de solicitar un cambio de tamaño permanente (póngase en contacto con el equipo de cuenta de Adobe) o intente reproducir el problema en el ensayo dedicado ejecutando una prueba de carga y optimizando las consultas, o código que reduzca la presión sobre los servicios. Para ver los pasos, consulte [Cloud for Adobe Commerce > Implementación de pruebas > Pruebas de carga y estrés](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) en nuestra documentación para desarrolladores.
