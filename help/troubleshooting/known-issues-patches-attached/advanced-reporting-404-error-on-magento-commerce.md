---
title: '[!DNL Advanced Reporting] Error 404 en Adobe Commerce'
description: Este artículo proporciona un parche para el problema de Adobe Commerce cuando un comerciante recibe un error 404 cuando intenta acceder a [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Una vez instalado este parche, los usuarios podrán acceder a [!DNL Advanced Reporting].
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] Error 404 en Adobe Commerce

Este artículo proporciona un parche para el problema de Adobe Commerce cuando un comerciante obtiene un error 404 al intentar acceder a [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Una vez instalado este parche, los usuarios podrán acceder a [!DNL Advanced Reporting].

Para comprobar si este parche puede resolver este problema, revise primero los registros con el siguiente comando:

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

Si ve el `Not valid cipher` error, aplicar el parche adjunto.

## Productos y versiones afectados

Adobe Commerce 2.2.6

## Problema

Un comerciante recibe un error 404 cuando intenta acceder [!DNL Advanced Reporting].

## Solución

Para solucionar el problema, aplique el parche adjunto a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo: [Descargar MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
