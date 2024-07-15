---
title: Vuelva al formulario de inicio de sesión de administrador de Commerce con el error "La sesión actual ha caducado".
description: '''Este artículo ofrece posibles soluciones para el problema de inicio de sesión del administrador de Commerce, que le redirige al formulario de inicio de sesión con el siguiente mensaje de error: *"La sesión actual ha caducado"*. Las soluciones incluyen comprobar los problemas de configuración de tiempo del servidor y cambiar la configuración de almacenamiento de la sesión".'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Vuelva al formulario de inicio de sesión de administrador de Commerce con el error &quot;La sesión actual ha caducado&quot;.

Este artículo ofrece las posibles soluciones para el problema de inicio de sesión del administrador de Commerce, en el que se le redirige de nuevo al formulario de inicio de sesión con el siguiente mensaje de error: *&quot;Su sesión actual ha caducado&quot;*. Las soluciones incluyen comprobar los problemas de configuración de tiempo del servidor y cambiar la configuración de almacenamiento de la sesión.

## Ediciones y versiones afectadas:

Todas las versiones y ediciones de Adobe Commerce

## Problema

<u>Pasos a seguir</u>:

1. Vaya a la página de administración de Commerce.
1. Introduzca sus credenciales de y haga clic en Iniciar sesión.

<u>Resultado esperado</u>:

Ha iniciado sesión en el administrador de Commerce.

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

Intente cambiar el almacenamiento de la sesión. Use la información del artículo [Cómo localizar los archivos de sesión](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) en nuestra documentación para desarrolladores para saber dónde se almacena su sesión y cámbiela editando el archivo `app/etc/env.php`.

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

* [Importar datos de archivos de configuración](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) en nuestra documentación para desarrolladores
* [Configurar Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) en nuestra documentación para desarrolladores
* [Vuelva a redirigir al formulario de inicio de sesión de administrador de Commerce con el error &quot;Su cuenta está temporalmente deshabilitada&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) en nuestra base de conocimiento de soporte
* [Vuelva al formulario de inicio de sesión sin errores al intentar iniciar sesión en el administrador de Commerce](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) en nuestra base de conocimiento de asistencia
