---
title: Los antiguos integrantes del equipo reciben correos electrónicos de notificación de Adobe Commerce Cloud
description: Este artículo proporciona una solución para Adobe Commerce en los correos electrónicos de notificación de infraestructura en la nube que se envían a los antiguos integrantes del equipo.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 075f295c5b600fcca9fbecc5aad20b0640d900f9
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Los antiguos integrantes del equipo reciben correos electrónicos de notificación de Adobe Commerce Cloud

Este artículo proporciona una solución para los casos en los que los integrantes del equipo que ya no están asociados con el proyecto siguen recibiendo notificaciones.

## Problema

Se ha enviado a su equipo un aviso de una interrupción detectada o de un problema importante relacionado con el proyecto o el entorno de la nube. Esto incluye a los miembros que ya no pueden estar asociados con su proyecto, como desarrolladores externos/de agencias o integradores de sistemas. Desea que estos usuarios dejen de recibir notificaciones.

## Solución

Existen dos maneras de detener las notificaciones eliminando al usuario(s) de su proyecto:

* Método 1: Uso de la nube [!DNL Project URL]. Consulte [Administrar el acceso de usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) en la guía de Commerce sobre la infraestructura en la nube para ver los pasos.
* Método 2: Uso de la nube de Magento [!DNL CLI]. Consulte [Administrar usuarios con [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) en la guía de Commerce sobre la infraestructura en la nube para ver los pasos.

Si ya se ha hecho esto y aún así las notificaciones por correo electrónico siguen incluyendo a esos usuarios, envíe un ticket de asistencia para solicitar que se eliminen de *[!UICONTROL Always CC]* configuración de en la cuenta.

## Lectura relacionada

* [Ver la función de proyecto de un usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user’s-project-role) en la guía de Commerce sobre la infraestructura en la nube.
* [Cómo incluir un miembro del equipo en las notificaciones de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) en la base de conocimientos de Commerce.
