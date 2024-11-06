---
title: 'Redirigir de nuevo al formulario de inicio de sesión de [!UICONTROL Commerce Admin] con el error "Su cuenta está temporalmente deshabilitada"'
description: '''Este artículo proporciona las posibles soluciones para el problema de inicio de sesión del administrador de Commerce, en el que se le redirige de nuevo al formulario de inicio de sesión con el siguiente mensaje de error: *"Su cuenta está temporalmente desactivada"*. La solución sugerida es comprobar y corregir la configuración de la base de datos de usuario administrador.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Volver a redirigir al formulario de inicio de sesión de [!UICONTROL Commerce Admin] con el error &quot;Su cuenta está temporalmente deshabilitada&quot;

Este artículo proporciona las posibles soluciones para el problema de inicio de sesión de [!UICONTROL Commerce Admin], donde se le redirigirá al formulario de inicio de sesión con el siguiente mensaje de error: *&quot;Su cuenta está temporalmente deshabilitada&quot;*. La solución sugerida es comprobar y corregir la configuración de la base de datos del usuario administrador.

## Ediciones y versiones afectadas:

Todas las versiones y ediciones de Adobe Commerce

## Problema

<u>Pasos a seguir</u>:

1. Vaya a la página **[!UICONTROL Commerce Admin]**.
1. Escriba sus credenciales y haga clic en **Iniciar sesión**.

<u>Resultado esperado</u>:

Ha iniciado sesión en [!UICONTROL Commerce Admin].

<u>Resultado real</u>:

Se le redirigirá de nuevo al formulario de inicio de sesión y se mostrará el siguiente mensaje de error: *&quot;Su cuenta está temporalmente deshabilitada. Inténtelo de nuevo más tarde&quot;*.

## Solución

1. Cree una copia de seguridad de base de datos.
1. Use una herramienta de base de datos como [[!DNL phpMyAdmin]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) o acceda a la base de datos manualmente desde la línea de comandos. En la tabla de la base de datos `admin_user`, para el registro de usuario administrador, compruebe si `is_active` está establecido en &quot;`1`&quot; y `lock_expires` es `NULL`. Restablezca estos valores si es necesario.

## Lectura relacionada

* [Redirigir de nuevo al formulario de inicio de sesión sin errores al intentar iniciar sesión en [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin)
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
