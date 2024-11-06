---
title: Correos electrónicos no enviados cuando se superan los créditos de SendGrid en Adobe Commerce
description: Este artículo proporciona una solución cuando los correos electrónicos no se envían porque ha superado el límite de créditos de SendGrid en Adobe Commerce.
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Correos electrónicos no enviados cuando se superan los créditos de SendGrid en Adobe Commerce

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Problema

Los créditos de SendGrid hacen referencia al número de correos electrónicos permitidos que se pueden enviar. Solo se pueden enviar 12 000 correos electrónicos al mes desde las ramas de integración y ensayo. Los créditos se renuevan a principios de mes, por lo que si se queda sin créditos, tendrá que esperar la renovación.

No existen límites estrictos en el número de correos electrónicos que se pueden enviar en producción, siempre y cuando la reputación del remitente sea superior al 95 %. La reputación se ve afectada por el número de correos electrónicos rechazados o rechazados y por si los registros de correo no deseado basados en DNS han marcado su dominio como una posible fuente de correo no deseado. En Producción, se asignan un total de 12 000 correos electrónicos al día, pero ese número se puede ampliar en función del número medio de correos electrónicos enviados en los cinco días anteriores.

## Cómo comprobar si se han superado tus créditos:

Arquitectura del plan Pro de Adobe Commerce en la infraestructura de la nube: Compruebe `/var/log/mail.log`; es posible que vea un mensaje como este:

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## Causa

Hay límites en la cantidad de correos electrónicos permitidos que se pueden enviar.

## Solución

* Si ve este mensaje en el entorno de producción, [envíe un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), proporcione el mensaje anterior y solicite que se aumenten los créditos.
* Si no ve este mensaje o está en Adobe Commerce en la arquitectura del plan de inicio de la infraestructura en la nube, [envíe también un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) y mencione que el archivo `mail.log` no indica que se hayan excedido los créditos.

## Lectura relacionada

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) en nuestra documentación para desarrolladores.
