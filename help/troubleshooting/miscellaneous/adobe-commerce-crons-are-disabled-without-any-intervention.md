---
title: Adobe Commerce [!DNL crons] deshabilitado sin intervención
description: Utilice este artículo para solucionar el problema en el cual  [!DNL crons] se deshabilitan sin intervención.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons desactivado sin intervención

Este artículo proporciona una solución para los casos en los que [!DNL crons] está deshabilitado sin intervención.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas [versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problema

Se han deshabilitado sus [!DNL crons] tras la implementación.

<u>Pasos a seguir</u>:

Implementar.

<u>Resultado esperado</u>:

Se están ejecutando sus [!DNL crons].

<u>Resultado real</u>:

Se han deshabilitado sus [!DNL crons] tras la implementación.

## Causa

Problema con la configuración de [!DNL OPcache].

## Solución

Actualice [!DNL ECE Tools] a la última versión [2002.1.13](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113).

## Lectura relacionada

* [Rendimiento lento, lento y de larga duración [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) en nuestra base de conocimiento de soporte.
* [[!DNL Cron] las tareas bloquean tareas de otros grupos](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) en nuestra base de conocimiento de soporte.
* [[!DNL Cron] el trabajo está atascado en estado de &quot;ejecución&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) en nuestra base de conocimiento de soporte.
