---
title: '''Redirigir de nuevo al formulario de inicio de sesión de [!UICONTROL Commerce Admin] con el error "Su sesión actual ha caducado"'
description: '''Este artículo ofrece posibles soluciones para el problema de inicio de sesión de [!UICONTROL Commerce Admin], en el cual se le redirigirá al formulario de inicio de sesión con el siguiente mensaje de error: *"La sesión actual ha caducado"*. Las soluciones incluyen comprobar los problemas de configuración de tiempo del servidor y cambiar la configuración de almacenamiento de la sesión".'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Volver a redirigir al formulario de inicio de sesión de [!UICONTROL Commerce Admin] con el error &quot;Su sesión actual ha caducado&quot;

Este artículo ofrece las posibles soluciones para el problema de inicio de sesión de [!UICONTROL Commerce Admin], en el que se le redirige de nuevo al formulario de inicio de sesión con el siguiente mensaje de error: *&quot;Su sesión actual ha caducado&quot;*. Las soluciones incluyen comprobar los problemas de configuración de tiempo del servidor y cambiar la configuración de almacenamiento de la sesión.

## Ediciones y versiones afectadas:

Todas las versiones y ediciones de Adobe Commerce

## Problema

<u>Pasos a seguir</u>:

1. Vaya a la página **[!UICONTROL Commerce Admin]**.
1. Escriba sus credenciales y haga clic en **Iniciar sesión**.

<u>Resultado esperado</u>:

Ha iniciado sesión en [!UICONTROL Commerce Admin].

<u>Resultado real</u>:

Se le redirigirá de nuevo al formulario de inicio de sesión y se mostrará el siguiente mensaje de error: *&quot;Su sesión actual ha caducado&quot;*.

## Causa

El problema puede deberse a dos posibles razones:

* Se ha corregido un problema con la configuración de tiempo del servidor
* Se ha corregido un problema con el almacenamiento de sesión

Consulte la siguiente sección para ver las soluciones.

## Solución

### Comprobar problemas de configuración de tiempo del servidor

Compruebe el registro de sesión creado en la tabla `admin_user_session`. Si los valores de `created_at` y/o `updated_at` son incorrectos, podría deberse al problema con la configuración de la hora del servidor. Pida al administrador del sistema del servidor que lo compruebe. Tenga en cuenta que la hora en la base de datos está configurada en UTC de forma predeterminada.

### Cambio del almacenamiento de sesión

Intente cambiar el almacenamiento de la sesión. Use la información del artículo [Cómo localizar los archivos de sesión](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/session-storage/sessions) en nuestra documentación para desarrolladores para saber dónde se almacena su sesión y cámbiela editando el archivo `app/etc/env.php`.

Por ejemplo, para iniciar el almacenamiento de la sesión en el sistema de archivos, cambie la sección `'session'` de la siguiente manera:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Ejecute el comando `bin/magento app:config:import` para importar los datos de configuración.


## Lectura relacionada

* [Importar datos de archivos de configuración](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/import-configuration) en nuestra documentación para desarrolladores
* [Configurar [!DNL Redis]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) en nuestra documentación para desarrolladores
* [Vuelva a redirigir al formulario de inicio de sesión de [!UICONTROL Commerce Admin] con el error &quot;Su cuenta está temporalmente deshabilitada&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error) en nuestra base de conocimiento de soporte
* [Vuelva al formulario de inicio de sesión sin errores al intentar iniciar sesión en [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin) en nuestra base de conocimiento de asistencia
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

