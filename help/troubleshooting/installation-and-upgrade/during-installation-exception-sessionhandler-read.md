---
title: Durante la instalación, excepción SessionHandler::read()
description: Este artículo proporciona una corrección para un error de excepción **SessionHandler::read()** durante la instalación de Adobe Commerce.
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%
---

# Durante la instalación, excepción SessionHandler::read()

Este artículo proporciona una corrección para un error de excepción **SessionHandler::read()** durante la instalación de Adobe Commerce.

## Problema

En el último paso de la instalación de Adobe Commerce, se muestra la siguiente excepción:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Este error solo se produce en versiones de código anteriores al 28 de septiembre de 2015. Si instala un código con fecha del 29 de septiembre o posterior, no debería producirse este error. Para obtener más información sobre las opciones de configuración de Redis, consulte [Configurar Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) en nuestra documentación para desarrolladores. Para obtener más información acerca de cómo especificar Redis mediante el programa de instalación desde la línea de comandos, consulte el [tema de instalación](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced) o el [tema de configuración de implementación](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/deployment) en nuestra documentación para desarrolladores.

## Causa

Esto sucede cuando el parámetro PHP `session.save_handler` está establecido en otro almacenamiento de sesión distinto de `files` (por ejemplo, `redis`, `memcached`, etc.). Se trata de un problema conocido que estamos tratando de resolver.

## Soluciones:

* Actualice el código de Adobe Commerce. Consulte [Guía de instalación > Actualización del software de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall) en nuestra documentación para desarrolladores.
* Utilice la siguiente solución con el código existente:

## Buscar `php.ini` {#locate-php-ini}

Busque `php.ini` introduciendo el siguiente comando:

```php
php -i | grep "Loaded Configuration File"
```

A continuación encontrará las ubicaciones habituales:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Solución {#workaround}

1. Como usuario con privilegios de `root`, abra `php.ini` en un editor de texto.
1. Buscar `session.save_handler`
1. Configúrelo de cualquiera de las siguientes maneras:
   * Para comentarlo:

     ```php
     ;session.save_path = <path>
     ```

   * Para establecerlo en una ruta del sistema de archivos:

     ```php
     session.save_handler = files
     ```
