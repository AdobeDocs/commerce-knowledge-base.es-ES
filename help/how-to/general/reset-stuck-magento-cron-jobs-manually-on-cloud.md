---
title: Restablecer manualmente los trabajos cron de Adobe Commerce atascados en la infraestructura en la nube
description: Los trabajos cron de Adobe Commerce en la infraestructura de la nube no terminan de ejecutarse, se quedan atascados e impiden que se ejecuten otros trabajos cron. Este artículo muestra cómo restablecer manualmente los trabajos cron atascados.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Restablecer manualmente los trabajos cron de Adobe Commerce atascados en la infraestructura en la nube

Los trabajos cron de Adobe Commerce en la infraestructura de la nube no terminan de ejecutarse, se quedan atascados e impiden que se ejecuten otros trabajos cron. Este artículo muestra cómo restablecer manualmente los trabajos cron atascados.

Utilice este comando con precaución. Recomendamos leer el artículo [Restablecer trabajos de cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=es) en nuestra base de conocimiento de soporte técnico para obtener más detalles.

## Pasos

>[!INFO]
>
>Desde [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html?lang=es#v2002.0.4) puede restablecer manualmente los trabajos cron atascados mediante un comando CLI a través del acceso SSH.

1. [SSH a su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=es).
1. Ejecutar este comando: `./vendor/bin/ece-tools cron:unlock`

## Advertencias

* El comando restablece **todos** los trabajos cron, incluidos los que se están ejecutando actualmente; **utilícelo solo en casos excepcionales**.
* Evite utilizar esta solución cuando se estén ejecutando indexadores.

## Léalo en nuestra base de conocimiento de asistencia:

[Restablecer trabajos cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=es)
