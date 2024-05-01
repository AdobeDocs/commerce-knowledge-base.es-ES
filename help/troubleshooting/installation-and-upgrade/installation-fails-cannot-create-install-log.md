---
title: La instalación falla; no se puede crear install.log
description: Este artículo proporciona una corrección para una instalación fallida debido a que el Asistente para la instalación no crea el archivo install.log durante la instalación.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# La instalación falla; no se puede crear install.log

Este artículo proporciona una corrección para una instalación fallida debido a que el Asistente para la instalación no crea el `install.log` durante la instalación.

## Problema

La ejecución de procesos de Adobe Commerce al mismo tiempo puede provocar problemas al crear el registro de instalación. (Por ejemplo, dos instalaciones diferentes en páginas de fichas independientes).

## Causa

Installation-failures-cannot-create-install.log Revise la configuración para `open_basedir` in `php.ini`. El Asistente de configuración utiliza el [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) Llamada PHP para obtener el valor del directorio temporal. If [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) está configurada para rechazar conexiones a un directorio especificado por `sys_get_temp_dir`, la instalación falla.
Revise la configuración para `open_basedir` in `php.ini`. El Asistente de configuración utiliza el [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) Llamada PHP para obtener el valor del directorio temporal. If [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) está configurada para rechazar conexiones a un directorio especificado por `sys_get_temp_dir`, la instalación falla.


## Solución

Para resolver el problema, cambie el valor de `open_basedir` y reinicie el servidor web.

Si no está seguro de cómo cambiar este valor, siga estos pasos:

1. Si aún no lo ha hecho, cree [phpinfo.php](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo).
1. Introduzca la siguiente URL en el campo de dirección o ubicación del navegador: `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Busque la ubicación de `php.ini`.     `php.ini` se suele especificar como **Archivo de configuración cargado** en los resultados mostrados.
1. Como usuario con privilegios de raíz, abra `php.ini` en un editor de texto.
1. Busque el valor de `open_basedir` y cambiarlo.
1. Guardar los cambios en `php.ini`.
1. Reinicie el servidor web.
