---
title: Los antiguos integrantes del equipo reciben correos electrónicos de notificación de Adobe Commerce Cloud
description: Este artículo proporciona una solución para Adobe Commerce en los correos electrónicos de notificación de infraestructura en la nube que se envían a los antiguos integrantes del equipo.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: bd199fac6d8f33491b9fa0f508b2bb52d56b46a5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Los antiguos integrantes del equipo reciben correos electrónicos de notificación de Adobe Commerce Cloud

Este artículo proporciona una solución para eliminar usuarios de la lista de destinatarios de correos electrónicos de notificación que son:

* Miembros anteriores del equipo que ya no están asociados con el proyecto.
* Integrantes del equipo actual que no deberían recibir las notificaciones.

## Problema

Se ha enviado a su equipo un aviso de una interrupción detectada o de un problema importante relacionado con el proyecto o el entorno de la nube. Esto incluye a los miembros que ya no pueden estar asociados con su proyecto, como desarrolladores externos/de agencias o integradores de sistemas. Desea que estos usuarios dejen de recibir notificaciones.

## Solución

>[!NOTE]
>
>Si es un desarrollador externo/de la agencia o un integrador de sistemas y ya no está asociado con el proyecto, debe ponerse en contacto con el Propietario del proyecto o el Administrador del proyecto de ese proyecto para obtener ayuda.

Existen dos maneras de detener las notificaciones eliminando al usuario(s) de su proyecto:

* Método 1: usar la nube [!DNL Project URL]. Consulte [Administrar el acceso de los usuarios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=es) en la guía de infraestructura de Commerce en la nube para ver los pasos.
* Método 2: usar la nube de Magento [!DNL CLI]. Consulte [Administrar usuarios con [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=es#manage-users-with-the-cli) en la guía de infraestructura de Commerce en la nube para ver los pasos.

Si ya se ha hecho esto y aún así las notificaciones por correo electrónico siguen incluyendo a esos usuarios, envíe un ticket de asistencia para solicitar que se eliminen de la configuración de *[!UICONTROL Always CC]* en la cuenta.

## Lectura relacionada

* [Ver el rol de proyecto de un usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=es#view-a-user&?lang=es#39;s-project-role) en la guía de infraestructura de Commerce en la nube.
* [Cómo incluir un miembro del equipo en las notificaciones de soporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html?lang=es) en la base de conocimientos de Commerce.
