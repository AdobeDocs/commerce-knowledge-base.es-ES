---
title: No se puede agregar el usuario al proyecto de nube de Adobe Commerce
description: Este artículo proporciona una solución para los casos en los que no pueda agregar un usuario a un proyecto de nube de Adobe Commerce.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# No se puede agregar el usuario al proyecto de nube de Adobe Commerce

Este artículo proporciona una solución para cuando intenta agregar un usuario a un proyecto de la nube, pero falla con un error: *El usuario XXX no existe*.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Este artículo proporciona una solución para los casos en los que no pueda agregar un usuario a un proyecto de nube de Adobe Commerce.

## Causa

Este es el comportamiento esperado. La cuenta del usuario debe crearse primero en https://accounts.magento.cloud y vincularse a su SSO de Adobe para que se añada como usuario al proyecto.

## Solución

1. Pida al usuario que inicie sesión en su cuenta en https://accounts.magento.cloud (ya debe haberse registrado para obtener una cuenta en adobe.com en esa dirección de correo electrónico). Crear o tener una cuenta en https://account.adobe.com no significa automáticamente que el usuario tenga una cuenta en https://accounts.magento.cloud) Nota: Si el usuario ha tenido una cuenta en account.magento.com o en accounts.magento.cloud antes de agosto de 2022, es posible que no tenga una cuenta con/en adobe.com a menos que la haya creado en agosto de 2022 o posterior. Si el usuario no tiene una cuenta de Adobe y no puede iniciar sesión, envíe un correo electrónico a [Grp-Magento-HelpCenterLoginIssues@adobe.com](mailto:Grp-Magento-HelpCenterLoginIssues@adobe.com) con los detalles.
1. El usuario debe ir a https://accounts.magento.cloud.
1. Una vez que lo hayan hecho, debería poder agregar al usuario al proyecto. Para ver los pasos, consulte [Adición de usuarios y administración del acceso](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) en nuestra Guía de infraestructura en la nube de Commerce.

## Lectura relacionada:

* [Administrar el acceso de usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) en nuestra Guía de infraestructura en la nube de Commerce.
* [No se puede iniciar sesión en la asistencia de Adobe Commerce o en la cuenta de la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
