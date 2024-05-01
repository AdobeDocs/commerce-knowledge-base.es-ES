---
title: La instalación se detiene en un 70%
description: Este artículo proporciona una corrección para los casos en los que la instalación se detiene en un 70 %.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

* La configuración de PHP para [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Valores de tiempo de espera para nginx y Varnish

## Solución:

Configure todas las siguientes opciones según corresponda.

### Todos los servidores web y Barnish {#all-web-servers-and-varnish}

1. Busque su `php.ini` uso de un [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) archivo.
1. Como usuario con `root` privilegios, abrir `php.ini` en un editor de texto.
1. Busque el `max_execution_time` configuración.
1. Cambie su valor a `18000` .
1. Guardar los cambios en `php.ini` y salga del editor de texto.
1. Reinicie Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Si utiliza nginx o Barniz, continúe con las siguientes secciones.

### nginx solamente {#nginx-only}

Si utiliza nginx, utilice nuestro incluido `nginx.conf.sample` o agregue una configuración de tiempo de espera en el archivo de configuración del host nginx a `location ~ ^/setup/index.php` como sigue:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Reiniciar nginx: `service nginx restart`

### Solo barniz {#varnish-only}

Si utiliza Barniz, edite `default.vcl` y añada un valor de límite de tiempo de espera a `backend` estrofa como sigue:

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
