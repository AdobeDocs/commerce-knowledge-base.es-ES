---
title: Vuelva al formulario de inicio de sesión del administrador de Commerce con el error "Su cuenta está temporalmente desactivada".
description: '''Este artículo proporciona las posibles soluciones para el problema de inicio de sesión del administrador de Commerce, en el que se le redirige de nuevo al formulario de inicio de sesión con el siguiente mensaje de error: *"Su cuenta está temporalmente desactivada"*. La solución sugerida es comprobar y corregir la configuración de la base de datos de usuario administrador.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Vuelva al formulario de inicio de sesión del administrador de Commerce con el error &quot;Su cuenta está temporalmente desactivada&quot;.

Este artículo proporciona las posibles soluciones para el problema de inicio de sesión del administrador de Commerce, en el que se le redirige de nuevo al formulario de inicio de sesión con el siguiente mensaje de error: *&quot;Su cuenta está temporalmente deshabilitada&quot;*. La solución sugerida es comprobar y corregir la configuración de la base de datos del usuario administrador.

## Ediciones y versiones afectadas:

Todas las versiones y ediciones de Adobe Commerce

## Problema

<u>Pasos a seguir</u>:

1. Vaya a la página de administración de Commerce.
1. Introduzca sus credenciales de y haga clic en Iniciar sesión.

<u>Resultado esperado</u>:

Ha iniciado sesión en el administrador de Commerce.

<u>Resultado real</u>:

Se le redirigirá de nuevo al formulario de inicio de sesión y se mostrará el siguiente mensaje de error: *&quot;Tu cuenta está temporalmente desactivada. Inténtelo de nuevo más tarde&quot;.*.

## Solución

1. Cree una copia de seguridad de base de datos.
1. Utilice una herramienta de base de datos como [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin), o acceda a la base de datos manualmente desde la línea de comandos. En el `admin_user` tabla de base de datos, para su registro de usuario administrador, compruebe si `is_active` se configura como &quot;`1`&quot; y `lock_expires` es `NULL`. Restablezca estos valores si es necesario.

## Lectura relacionada en nuestra base de conocimiento de soporte

* [Volver a dirigir al formulario de inicio de sesión sin errores al intentar iniciar sesión en el administrador de Commerce](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md)
