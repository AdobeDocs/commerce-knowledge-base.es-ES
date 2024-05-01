---
title: Monitorización de la hoja de datos para [!DNL Adobe Commerce on cloud pro infrastructure]
description: Este documento proporciona información sobre la monitorización y las notificaciones de la infraestructura de Adobe Commerce.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 4926bcff19b8c4c7e2a9a9dfb0cb1fc72a9821ba
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Monitorización de la hoja de datos para [!DNL Adobe Commerce on cloud pro infrastructure]

Este documento proporciona información sobre la monitorización y las notificaciones de la infraestructura de Adobe Commerce.

La monitorización permite a los comerciantes, integradores de sistemas y equipos internos de Adobe solucionar problemas de disponibilidad del sitio y espacio en disco insuficiente.

## Solución y resolución de problemas

Las instancias de Adobe Commerce generalmente contienen código personalizado y configuraciones. El Adobe no admite ni resuelve problemas con el código personalizado y las configuraciones. El Adobe ayuda a los comerciantes a solucionar problemas e identificar problemas en nuestra base de conocimientos, y proporciona soluciones recomendadas y prácticas recomendadas para prevenir y resolver problemas. Recomendamos a los comerciantes y socios que utilicen las tablas siguientes para comprender qué se supervisa y quién es el responsable de la resolución.

Cuando se activan las notificaciones, el equipo de asistencia de Adobe Commerce clasifica el problema. Como parte de la clasificación, se analizan los registros de errores y otros recursos. En función de la clasificación, se [!DNL Zendesk] los tickets de asistencia se crean para comerciantes o socios (en caso de actualizaciones personalizadas) o para los equipos internos de Adobe para resolver el problema.

## Adobe Commerce: monitorización predeterminada

Los eventos siguientes se supervisan y el equipo de Adobe Commerce toma las medidas necesarias para resolver y comunicar los problemas identificados.

## Monitorización de disponibilidad del sitio

| Disponibilidad del sitio | Descripción |
|------------|------------|
| **Objetivo de monitorización** | Para rastrear la disponibilidad del sitio. |
| **Instrumentado el** | Único [!DNL URL] seleccionado para alta [!DNL SLA]. |
| **Descripción** | La disponibilidad del sitio se determina según los umbrales configurados en torno a la métrica. La notificación de la interrupción del sitio se activa si la comprobación falla durante 10 minutos y no hay ninguna implementación activa en curso. |
| **Destinatario de notificación** | Comerciante/Socio y Adobe. |
| **Acción por Adobe** | Responsable de la prueba y corrección si el problema se encuentra en la infraestructura de Adobe Commerce. |
| **Acción del comerciante** | Responsable de solucionar el problema si es debido a cambios o a un código personalizado introducido por un comerciante o socio. Para solucionar problemas, consulte: [Solucionador de problemas de Site Down](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## Monitorización de Diskspace

| Monitorización de Diskspace | Descripción |
|------------|------------|
| **Objetivo de monitorización** | Para realizar un seguimiento del uso del espacio en disco. |
| **Instrumentado el** | [!DNL MySQL] particiones de disco y de medios. |
| **Métrica** | El espacio libre en disco se monitoriza cada minuto en el host. Se genera una advertencia si solo queda un 5% o 2 GB de espacio libre. El umbral esencial establecido para el espacio libre restante es del 2 % o 1 GB. |
| **Descripción** | La notificación se envía en función de los umbrales configurados en torno al espacio en disco libre para el host. Espacio en disco adicional se agrega automáticamente una vez al montaje correspondiente ([!DNL MySQL] o medios) para evitar una interrupción del sitio y dar al comerciante tiempo para borrar el espacio en disco o identificar y resolver cualquier código o registro que cause un rápido aumento del uso del disco. |
| **Destinatario de notificación** | Comerciante/Socio y Adobe. |
| **Acción por Adobe** | Elevar automáticamente el ticket de soporte y se agrega automáticamente espacio en disco adicional al montaje correspondiente ([!DNL MySQL] o medios) para evitar una interrupción del sitio. |
| **Acción del comerciante** | Para recibir alertas de espacio en disco de nivel de advertencia continua, consulte: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: alerta de advertencia de disco](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-warning-alert.html)</li><li>[[!DNL Managed alerts for Adobe Commerce]: alerta de disco crítico](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-critical-alert.html) </li></ul> |
