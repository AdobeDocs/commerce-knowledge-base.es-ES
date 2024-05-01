---
title: Resolución de un error de desplazamiento no válido
description: Este artículo proporciona una solución para los casos en los que, en Adobe Commerce 2.1 o posterior, reciba un error Resolver un desplazamiento no válido al crear un nuevo producto en el administrador de Commerce.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Resolución de un error de desplazamiento no válido

Este artículo proporciona una solución para los casos en los que, en Adobe Commerce 2.1 o posterior, reciba un error Resolver un desplazamiento no válido al crear un nuevo producto en el administrador de Commerce.

En Adobe Commerce 2.1 o posterior, al crear un nuevo producto en el administrador de Commerce, puede aparecer el siguiente error:

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## Detalle

Adobe Commerce 2.1 y versiones posteriores utilizan comentarios de código PHP en la `getDocComment` llamada de validación en [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) Método en `Magento\Framework\Api\ExtensionAttributesFactory.php`.

Si habilitó la OPcache de PHP (que recomendamos), se muestra este error porque, de forma predeterminada, la configuración de OPcache [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) está deshabilitada.

## Solución

Para resolver el problema, busque los ajustes de configuración de la caché de OP y habilite `opcache.save_comments` como sigue:

### Paso 1: Localice la configuración de OPcache

#### Para buscar los valores de configuración de OPcache:

La configuración de la caché de PHP OP generalmente se encuentra en `php.ini` o `opcache.ini`. La ubicación puede depender de su sistema operativo y versión de PHP. El archivo de configuración de OPcache puede tener un `[opcache]` sección o configuración como `opcache.enable`.

Siga estas directrices para encontrarlo:

* Servidor web Apache:<br>

Para Ubuntu con Apache, la configuración de OPcache generalmente se encuentra en `php.ini`.<br>
Para CentOS con Apache o nginx, la configuración de OPcache generalmente se encuentra en `/etc/php.d/opcache.ini`.<br>
Si no es así, utilice el siguiente comando para localizarlo:

```bash
    $ sudo find / -name 'opcache.ini'
```

* Servidor web nginx con PHP-FPM: `/etc/php5/fpm/php.ini`.

Si tiene más de uno `opcache.ini`, modifique todos ellos.


### Paso 2: Habilitar `opcache.save_comments`

1. Abra el archivo de configuración de OPcache en un editor de texto.
1. Localizar `opcache.save_comments` y quite los comentarios, si es necesario.
1. Asegúrese de que su valor está establecido en `1`.
1. Guarde los cambios y salga del editor de texto.
1. Reinicie el servidor web:

   * Apache, Ubuntu: `service apache2 restart`
   * Apache, CentOS: `service httpd restart`
   * nginx, Ubuntu y CentOS: `service nginx restart`

1. Volver a generar la configuración de ID y todas las clases que faltan que se pueden generar automáticamente:

```bash
    $ bin/magento setup:di:compile`
```
