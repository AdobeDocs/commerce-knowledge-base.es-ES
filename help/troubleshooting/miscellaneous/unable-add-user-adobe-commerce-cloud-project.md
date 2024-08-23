---
title: No se puede agregar el usuario al proyecto de nube de Adobe Commerce
description: Este artículo proporciona una solución para los casos en los que no pueda agregar un usuario a un proyecto de nube de Adobe Commerce.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: af74d944553c34da2ac8343695bca49f971bc4e5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# No se puede agregar el usuario al proyecto de nube de Adobe Commerce

Este artículo proporciona una solución para cuando intenta agregar un usuario a un proyecto en la nube, pero falla con un error: *El usuario XXX no existe*.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Este artículo proporciona una solución para los casos en los que no pueda agregar un usuario a un proyecto de nube de Adobe Commerce.

## Causa

Este es el comportamiento esperado. La cuenta del usuario debe crearse primero en https://accounts.magento.cloud y vincularse a su SSO de Adobe para que se añada como usuario al proyecto.

## Solución

1. Pida al usuario que inicie sesión en su cuenta en https://accounts.magento.cloud (ya debe haberse registrado para obtener una cuenta en adobe.com en esa dirección de correo electrónico). Crear o tener una cuenta en https://account.adobe.com no significa automáticamente que el usuario tendría una cuenta en https://accounts.magento.cloud)
Nota: Si el usuario ha tenido una cuenta en account.magento.com o en accounts.magento.cloud antes de agosto de 2022, es posible que no tenga una cuenta con/en adobe.com a menos que la haya creado en agosto de 2022 o posterior. Si el usuario no tiene una cuenta de Adobe y no puede iniciar sesión, [envíe una solicitud de soporte técnico](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) a https://experienceleague.adobe.com/home#support y proporcione los detalles (Motivo del problema = Administración de usuarios).
1. El usuario debe ir a https://accounts.magento.cloud.
1. Una vez que lo hayan hecho, debería poder agregar al usuario al proyecto. Para ver los pasos, consulte [Agregar usuarios y administrar el acceso](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) en nuestra Guía de infraestructura de Commerce en la nube.

## Lectura relacionada:

* [Administrar el acceso de los usuarios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) en nuestra Guía de infraestructura de Commerce en la nube.
* [No se puede iniciar sesión en la cuenta de nube o en la asistencia de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
