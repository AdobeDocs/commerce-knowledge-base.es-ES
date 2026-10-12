---
title: La instalación falla; no se puede crear install.log
description: Este artículo proporciona una corrección para una instalación fallida debido a que el Asistente para la instalación no crea el archivo install.log durante la instalación.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%
---
# La instalación falla; no se puede crear install.log

Este artículo proporciona una corrección de un error en la instalación debido a que el Asistente para la instalación no creó `install.log` durante la instalación.

## Problema

La ejecución de procesos de Adobe Commerce al mismo tiempo puede provocar problemas al crear el registro de instalación. (Por ejemplo, dos instalaciones diferentes en páginas de fichas independientes).

## Causa

Installation-failures-cannot-create-install.log
Revise la configuración de `open_basedir` en `php.ini`. El Asistente para la instalación usa la llamada PHP [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) para obtener el valor del directorio temporal. Si [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) está configurado para rechazar conexiones a un directorio especificado por `sys_get_temp_dir`, la instalación falla.
Revise la configuración de `open_basedir` en `php.ini`. El Asistente para la instalación usa la llamada PHP [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) para obtener el valor del directorio temporal. Si [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) está configurado para rechazar conexiones a un directorio especificado por `sys_get_temp_dir`, la instalación falla.


## Solución

Para resolver el problema, cambie el valor de `open_basedir` y reinicie el servidor web.

Si no está seguro de cómo cambiar este valor, siga estos pasos:

1. Si aún no lo has hecho, crea [phpinfo.php](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. Escriba la siguiente dirección URL en el campo de dirección o ubicación del explorador: `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Busque la ubicación de `php.ini`. `php.ini` se suele especificar como **Archivo de configuración cargado** en los resultados mostrados.
1. Como usuario con privilegios de root, abra `php.ini` en un editor de texto.
1. Busque el valor de `open_basedir` y cámbielo.
1. Guarde los cambios en `php.ini`.
1. Reinicie el servidor web.
