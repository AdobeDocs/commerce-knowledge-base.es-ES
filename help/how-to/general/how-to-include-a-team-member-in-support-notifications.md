---
title: Cómo incluir un miembro del equipo en las notificaciones de asistencia
description: Este artículo explica cómo incluir un miembro del equipo en las notificaciones de asistencia.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Cómo incluir un miembro del equipo en las notificaciones de asistencia

Este artículo explica cómo incluir a un miembro del equipo para que reciba automáticamente las actualizaciones de soporte a través de las notificaciones por correo electrónico.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todo [versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Causa

* El miembro del equipo no se ha agregado al [!DNL cloud project] con los privilegios necesarios.
* El miembro del equipo no tiene una cuenta de soporte técnico.

## Solución

1. Vaya a la **[!DNL Cloud Project URL]** (Ejemplo: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Compruebe si el miembro del equipo se ha agregado al proyecto y si es un [!DNL Super User].

Si no es necesario [!DNL cloud project] Acceda a, envíe un [Solicitud de asistencia en el Centro de asistencia de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para automáticamente CC: les en todos los tickets, y también proporcione su **[!DNL MAGE ID]** (si está disponible).

Si no se han agregado al proyecto, deberá agregarlos como un [!DNL Super User] y conceder [!DNL Shared Access]:

* [Administrar el acceso de usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) en nuestra guía del usuario.
* [No se puede agregar el usuario al proyecto de nube de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) en nuestra Base de conocimiento de Commerce.
* [Guía del usuario del Centro de ayuda de Adobe Commerce: Acceso compartido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) en nuestra Base de conocimiento de Commerce.

Si se han agregado al [!DNL cloud project], pero no tiene el [!DNL Super User role], actualice su [!DNL role] en consecuencia, en [Administrar el acceso de usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Lectura relacionada

[Los antiguos integrantes del equipo reciben correos electrónicos de notificación de Adobe Commerce Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
