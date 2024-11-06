---
title: La instalación se detiene en un 70%
description: Este artículo proporciona una corrección para los casos en los que la instalación se detiene en un 70 %.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# La instalación se detiene en un 70%

Este artículo proporciona una corrección para los casos en los que la instalación se detiene en un 70 %.

## Problema

Durante la instalación con el Asistente para la instalación, el proceso se detiene en un 70% (con o sin datos de ejemplo). No se muestran errores en la pantalla.

## Causa

Las causas comunes de este problema incluyen:

* Configuración de PHP para [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Valores de tiempo de espera para nginx y Varnish

## Solución:

Configure todas las siguientes opciones según corresponda.

### Todos los servidores web y Barnish {#all-web-servers-and-varnish}

1. Busque su `php.ini` usando un archivo de [`phpinfo.php`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. Como usuario con privilegios de `root`, abra `php.ini` en un editor de texto.
1. Busque la configuración `max_execution_time`.
1. Cambie su valor a `18000`
1. Guarde los cambios en `php.ini` y salga del editor de texto.
1. Reinicie Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Si utiliza nginx o Barniz, continúe con las siguientes secciones.

### nginx solamente {#nginx-only}

Si usa nginx, use nuestro `nginx.conf.sample` incluido o agregue una configuración de tiempo de espera en el archivo de configuración del host nginx a la sección `location ~ ^/setup/index.php` de la siguiente manera:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Reiniciar nginx: `service nginx restart`

### Solo barniz {#varnish-only}

Si usa Barnish, edite `default.vcl` y agregue un valor de límite de tiempo de espera a la estrofa `backend` de la siguiente manera:

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

Reinicie Barniz.

```php
service varnish restart
```
