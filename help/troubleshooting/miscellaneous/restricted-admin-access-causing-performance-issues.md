---
title: Acceso de administrador restringido que causa problemas de rendimiento
description: Este artículo proporciona soluciones para los casos en los que el rendimiento se ve afectado negativamente por el uso de [Funciones de administrador con ámbito de función restringido por sitio web](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) en nuestra guía del usuario.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Acceso de administrador restringido que causa problemas de rendimiento

Este artículo proporciona soluciones para los casos en que el rendimiento se vea afectado negativamente por el uso de [roles de administrador con un ámbito de rol restringido por el sitio web](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) en nuestra guía del usuario.

## Productos y versiones afectados

* Adobe Commerce local 2.2.x, 2.3.x
* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x

## Problema

Cuando un usuario administrador, con el ámbito de función restringido por el sitio web, realiza operaciones en el panel de administración (incluido el inicio de sesión, el guardado de productos, etc.), Adobe Commerce vuelve a crear la caché almacenada. La reconstrucción de la caché afecta negativamente al rendimiento y puede provocar una interrupción del sitio, especialmente durante las horas laborables o de alto tráfico.

El problema se corrige en Adobe Commerce 2.2.10 y 2.3.3.

## Solución

A continuación se indican las opciones para evitar el problema:

* Actualice la versión de la aplicación de Adobe Commerce a 2.2.10 o 2.3.3. (para obtener instrucciones, consulte [Actualizar Adobe Commerce en la versión de infraestructura en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) en nuestra documentación para desarrolladores).
* Evite restringir el ámbito de la función de usuario administrador por sitio web, si es posible.
* [Envíe un ticket de soporte al Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar un parche, si está disponible.

## Lectura relacionada

* [Funciones de usuario](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles) en nuestra guía de usuario.
