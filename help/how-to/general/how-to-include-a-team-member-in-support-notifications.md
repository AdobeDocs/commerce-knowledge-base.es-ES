---
title: Cómo incluir un miembro del equipo en las notificaciones de asistencia
description: Este artículo explica cómo incluir un miembro del equipo en las notificaciones de asistencia.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 771793d45000e65c1bf41137cd984d2977b0a9ff
workflow-type: tm+mt
source-wordcount: '195'
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

Si no se han agregado al proyecto, deberá agregarlos como [!DNL Super User] y conceder a [!DNL Shared Access]:

* [Administrar el acceso de los usuarios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=es) en nuestra guía del usuario.
* [No se puede agregar un usuario al proyecto de nube de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html?lang=es) en nuestra Base de conocimiento de Commerce.
* [Guía del usuario del Centro de ayuda de Adobe Commerce: Acceso compartido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=es#shared-access) en nuestra Base de conocimiento de Commerce.

Si se han agregado a [!DNL cloud project], pero no tienen [!DNL Super User role], actualice [!DNL role] según corresponda en [Administrar acceso de usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=es).

## Lectura relacionada

[Los antiguos integrantes del equipo reciben correos electrónicos de notificación de Adobe Commerce Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html?lang=es)
