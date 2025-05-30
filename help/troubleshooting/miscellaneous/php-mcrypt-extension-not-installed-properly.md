---
title: La extensión PHP mcrypt no está instalada correctamente
description: La extensión PHP mcrypt no está instalada correctamente
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# La extensión PHP mcrypt no está instalada correctamente

>[!WARNING]
>
>NOTA: La función de biblioteca mcrypt estaba [obsoleta en PHP 7.1 y se eliminó de PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php).

## Detalle

Los errores pueden incluir lo siguiente:

```php
exception 'Exception' with message 'PHP Warning: PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] exception 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://experienceleague.adobe.com/es/docs/commerce-operations/operational-playbook/glossary#extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## Descripción

Particularmente en los sistemas de desarrollo que incluyen una &quot;pila&quot; de Linux/Apache/MySQL/PHP (LAMP) separada del sistema operativo, es posible que mcrypt no esté instalado o que esté instalado en la ruta de la pila LAMP pero no en la ruta del sistema operativo.

Como resultado, el instalador de Adobe Commerce no puede localizar la extensión y la instalación falla.

## Sugerencia

Determine si la extensión mcrypt se carga de alguna de las siguientes maneras:

* Configure un archivo [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) en el directorio raíz del servidor web y examine el resultado en un explorador web.
* Ejecute el siguiente comando:    `$ php -r "phpinfo();" | grep mcrypt`

Si mcrypt es *no* instalado, se muestran mensajes similares a los siguientes:

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

En algunos casos, es posible que tenga que instalar el software de Adobe Commerce desde la [línea de comandos](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/advanced) y especificar la ruta completa a la pila LAMP que tiene instalado mcrypt.
