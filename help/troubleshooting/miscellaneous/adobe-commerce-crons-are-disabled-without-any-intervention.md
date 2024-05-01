---
title: Adobe Commerce [!DNL crons] desactivado sin intervención
description: Utilice este artículo para solucionar el problema donde [!DNL crons] están deshabilitadas sin intervención.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons desactivado sin intervención

Este artículo proporciona una solución para cuando [!DNL crons] están deshabilitadas sin intervención.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todo [versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problema

Su [!DNL crons] se desactivan después de la implementación.

<u>Pasos a seguir</u>:

Implementar.

<u>Resultado esperado</u>:

Su [!DNL crons] se están ejecutando.

<u>Resultado real</u>:

Su [!DNL crons] se desactivan después de la implementación.

## Causa

Problema con el [!DNL OPcache] configuración.

## Solución

Actualizar [!DNL ECE Tools] a la última versión [2002.1.13](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## Lectura relacionada

* [Rendimiento lento, funcionamiento lento y prolongado [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) en nuestra base de conocimiento de soporte.
* [[!DNL Cron] las tareas bloquean tareas de otros grupos](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) en nuestra base de conocimiento de soporte.
* [[!DNL Cron] el trabajo está atascado en estado &quot;en ejecución&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) en nuestra base de conocimiento de soporte.
