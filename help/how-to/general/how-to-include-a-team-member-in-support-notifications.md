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

* Adobe Commerce en la infraestructura en la nube, todas [versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Causa

* El miembro del equipo no se ha agregado a [!DNL cloud project] con los privilegios necesarios.
* El miembro del equipo no tiene una cuenta de soporte técnico.

## Solución

1. Vaya a **[!DNL Cloud Project URL]** (ejemplo: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Compruebe si el miembro del equipo se ha agregado al proyecto y es un [!DNL Super User].

Si no requieren acceso de [!DNL cloud project], envía una [solicitud de asistencia en el Centro de asistencia de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para que se los incluya automáticamente en todos los tickets y también proporciona su **[!DNL MAGE ID]** (si está disponible).

Si no se han agregado al proyecto, deberá agregarlos como [!DNL Super User] y conceder a [!DNL Shared Access]:

* [Administrar el acceso de los usuarios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) en nuestra guía del usuario.
* [No se puede agregar un usuario al proyecto de nube de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) en nuestra Base de conocimiento de Commerce.
* [Guía del usuario del Centro de ayuda de Adobe Commerce: Acceso compartido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) en nuestra Base de conocimiento de Commerce.

Si se han agregado a [!DNL cloud project], pero no tienen [!DNL Super User role], actualice [!DNL role] según corresponda en [Administrar acceso de usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Lectura relacionada

[Los antiguos integrantes del equipo reciben correos electrónicos de notificación de Adobe Commerce Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
