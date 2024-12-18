---
title: "Alertas administradas en Adobe Commerce: alertas de MariaDB"
description: 'Este artículo proporciona pasos para solucionar problemas cuando recibe alertas MariaDB para Adobe Commerce en New Relic. Las alertas de MariaDB supervisan la carga de consultas alta, así como las consultas de lenguaje de manipulación de datos (DML) excesivas. Ambos pueden llevar a una experiencia del usuario degradada o incluso a un tiempo de inactividad. Puede recibir cuatro tipos de alertas:'
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Alertas administradas en Adobe Commerce: alertas de MariaDB

Este artículo proporciona pasos para la resolución de problemas cuando recibe alertas MariaDB para Adobe Commerce en New Relic. Las alertas de MariaDB supervisan la carga de consultas alta, así como las consultas de lenguaje de manipulación de datos (DML) excesivas. Ambos pueden llevar a una experiencia del usuario degradada o incluso a un tiempo de inactividad. Puede recibir cuatro tipos de alertas:

* Advertencia de consultas DML
* Consultas DML Críticas

## **Productos y versiones afectados**

Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube

## Problema

Recibirá una alerta administrada en New Relic si se ha registrado en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas se desarrollaron por Adobe para ofrecer a los clientes un conjunto estándar con las perspectivas de Soporte e Ingeniería.

**Hacer!**

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Guía de instalación > Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt).
* Finalice los scripts, como las importaciones, que puedan ser la causa de la alerta si el rendimiento del sitio se ve afectado.

**¡No!**

* Ejecute indexadores o crones adicionales que puedan causar un estrés adicional en MariaDB.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché.

## Solución

**Consultas DML (consultas que modifican la base de datos mediante UPDATE, INSERT y DELETE)**

Si recibe una alerta de consultas críticas de DML, comience en el paso uno. Si recibe una alerta de advertencia de consultas DML, comience en el paso dos.

1. Compruebe si existe un ticket de asistencia de Adobe Commerce. Para ver los pasos, consulte nuestra base de conocimiento [Seguimiento de los tickets de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). Es posible que el equipo de asistencia haya recibido una alerta de umbral de New Relic, haya creado un ticket y haya empezado a trabajar en el problema. Si no existe ningún ticket, cree uno. El ticket debe tener la siguiente información:
1. Motivo del contacto: seleccione &quot;Alerta de New Relic MariaDB recibida&quot;.
1. Descripción de la alerta.
1. [Vínculo a incidente de New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Esto se incluye en [Alertas administradas para Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Para identificar el origen del problema, intente identificar las consultas DML:
1. Revise las operaciones de la base de datos mediante los pasos de la página [Páginas de IU de APM > Supervisión > Bases de datos](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) de New Relic.
1. Ordene por CALL COUNT y luego OPERATION. Revise las operaciones INSERT, DELETE y UPDATE.
1. Busque una media alta.
1. Haga clic para buscar llamadores de operaciones de base de datos. Esto identificará las transacciones que utilizan esa consulta por tiempo.
1. Busque optimizaciones de código u optimizaciones operativas:
1. Optimizaciones de código: busque optimizar las consultas con inserciones/actualizaciones masivas, minimizando el uso del índice o restringiendo el código.
1. Optimizaciones operativas: descargue las modificaciones de datos que requieren muchos recursos para reducir los tiempos de tráfico.
1. Optimizaciones adicionales: Asegúrese de que está en la última versión de ECE-Tools. Para ver los pasos, consulte [Cloud for Adobe Commerce > Actualizar ece-tools version](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) en nuestra documentación para desarrolladores.

## Lectura relacionada

* Para investigar otros problemas comunes de MariaDB, consulte [Problemas más comunes de la base de datos para Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Para investigar las prácticas recomendadas de la base de datos, consulte [Prácticas recomendadas de la base de datos para Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
