---
title: '''[!DNL SendGrid] limitación de archivos para Adobe Commerce Cloud'
description: Este artículo proporciona una solución al problema  [!DNL SendGrid] limitación para Adobe Commerce en la infraestructura en la nube.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# [!DNL SendGrid] limitación para Adobe Commerce Cloud

Este artículo proporciona algunas soluciones para lo siguiente [!DNL SendGrid] limitación para Adobe Commerce en la infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problema

Intenta enviar archivos adjuntos grandes en correos electrónicos y ve estos errores de registro:

Entrada `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

Entrada `/var/log/exception.log`

Producción:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Ensayo:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Ensayo2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Causa

[!DNL SendGrid] tiene una limitación del sistema de 30 MB para el correo electrónico. Se recomienda no utilizar archivos adjuntos que superen los 10 Mb. Consulte [Enviando archivos adjuntos](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) en la documentación de SendGrid para obtener más información.

## Solución

* No utilice accesorios superiores a 6 Mb o 10 Mb.
* Considere el uso de un servidor SMTP remoto en la instancia de Adobe Commerce. Para ver los pasos, consulte [Configurar comunicaciones por correo electrónico](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) en nuestra Guía de sistemas de administración.
* Vuelva a configurar el servidor para que los archivos se puedan guardar en el módulo y, a continuación, adjunte el vínculo a los archivos de los correos electrónicos.

## Lectura relacionada

* [[!DNL SendGrid] servicio de correo electrónico](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html) en nuestra Guía de infraestructura en la nube de Commerce.
