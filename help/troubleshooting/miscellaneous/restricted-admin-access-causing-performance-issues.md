---
title: Acceso de administrador restringido que causa problemas de rendimiento
description: Este artículo proporciona soluciones para los casos en los que el rendimiento se ve afectado negativamente por el uso de [Funciones de administrador con ámbito de función restringido por sitio web](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) en nuestra guía del usuario.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Acceso de administrador restringido que causa problemas de rendimiento

Este artículo proporciona soluciones para los casos en los que el rendimiento se ve afectado negativamente por el uso de [Funciones de administrador con ámbito de función restringido por sitio web](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) en nuestra guía del usuario.

## Productos y versiones afectados

* Adobe Commerce local 2.2.x, 2.3.x
* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x

## Problema

Cuando un usuario administrador, con el ámbito de función restringido por el sitio web, realiza operaciones en el panel de administración (incluido el inicio de sesión, el guardado de productos, etc.), Adobe Commerce vuelve a crear la caché almacenada. La reconstrucción de la caché afecta negativamente al rendimiento y puede provocar una interrupción del sitio, especialmente durante las horas laborables o de alto tráfico.

El problema se corrige en Adobe Commerce 2.2.10 y 2.3.3.

## Solución

A continuación se indican las opciones para evitar el problema:

* Actualice la versión de la aplicación de Adobe Commerce a 2.2.10 o 2.3.3. (para obtener instrucciones, consulte la [Actualización de Adobe Commerce en la versión de infraestructura en la nube](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade.html) en nuestra documentación para desarrolladores).
* Evite restringir el ámbito de la función de usuario administrador por sitio web, si es posible.
* [Enviar un ticket de asistencia al Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), para solicitar un parche, si está disponible.

## Lectura relacionada

* [Funciones de usuario](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html) en nuestra guía del usuario.
