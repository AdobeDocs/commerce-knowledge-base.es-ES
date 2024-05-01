---
title: Durante la instalación, excepción SessionHandler::read()
description: "Este artículo proporciona una corrección para un error de excepción **SessionHandler::read()** durante la instalación de Adobe Commerce."
source-git-commit: 5cec04f8c4f80d34fc26b06eb929960ce21e2dc0
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Durante la instalación, excepción SessionHandler::read()

Este artículo proporciona una corrección para una excepción **SessionHandler::read()** error durante la instalación de Adobe Commerce.

## Problema

En el último paso de la instalación de Adobe Commerce, se muestra la siguiente excepción:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Este error solo se produce en versiones de código anteriores al 28 de septiembre de 2015. Si instala un código con fecha del 29 de septiembre o posterior, no debería producirse este error. Para obtener más información sobre las opciones de configuración de Redis, consulte [Configurar Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) en nuestra documentación para desarrolladores. Para obtener más información acerca de cómo especificar Redis mediante el instalador de la línea de comandos, vea la [tema de instalación](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-install.html) o el [tema de configuración de implementación](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp) en nuestra documentación para desarrolladores.

## Causa

Esto sucede cuando su `session.save_handler` El parámetro PHP está configurado para otro almacenamiento de sesión que `files` (por ejemplo, `redis`, `memcached`, etc.). Se trata de un problema conocido que estamos tratando de resolver.

## Soluciones:

* Actualice el código de Adobe Commerce. Consulte [Guía de instalación > Actualización del software de Adobe Commerce](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall.html#instgde-install-magento-update) en nuestra documentación para desarrolladores.
* Utilice la siguiente solución con el código existente:

## Localizar `php.ini` {#locate-php-ini}

Localizar `php.ini` introduciendo el siguiente comando:

```php
php -i | grep "Loaded Configuration File"
```

A continuación encontrará las ubicaciones habituales:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Solución {#workaround}

1. Como usuario con `root` privilegios, abrir `php.ini` en un editor de texto.
1. Localizar `session.save_handler`
1. Configúrelo de cualquiera de las siguientes maneras:
   * Para comentarlo:

     ```php
     ;session.save_path = <path>
     ```

   * Para establecerlo en una ruta del sistema de archivos:

     ```php
     session.save_handler = files
     ```
