---
title: Errores de configuración de PHP
description: Este artículo proporciona soluciones para los errores de configuración de PHP.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Errores de configuración de PHP

Este artículo proporciona soluciones para los errores de configuración de PHP.

## Error de límite de memoria PHP

Las comprobaciones de disponibilidad garantizan que tenga al menos 1 GB de memoria reservados para los procesos PHP. Esta configuración debería ser suficiente para la mayoría de las instalaciones, incluida la instalación de datos de muestra opcionales. Sin embargo, se recomiendan al menos 2 GB para la depuración.

Para aumentar el límite de memoria PHP:

1. Inicie sesión en el servidor de Adobe Commerce.
1. Busque el archivo `php.ini` con el siguiente comando:

   ```
   bash    $ php --ini
   ```

1. Como usuario con privilegios de `root`, use un editor de texto para abrir el `php.ini` especificado por `Loaded Configuration File`.
1. Busque `memory_limit`.
1. Cámbielo a un valor de `2GB` para su uso y depuración normales.
1. Guarde los cambios en `php.ini` y salga del editor de texto.
1. Reinicie el servidor web. A continuación se muestran ejemplos:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (tanto CentOS como Ubuntu): `service nginx restart`

1. Vuelva a intentar la instalación.

## error de max-input-vars debido a formularios grandes

Las configuraciones con un número elevado de vistas de tienda, productos, atributos u opciones pueden generar formularios que superen el límite preestablecido de PHP. Si el número de valores enviados supera el límite de `max-input-vars` establecido en `php.ini` (el valor predeterminado es 1000), los datos restantes no se transfieren y los valores de la base de datos no se actualizan. Cuando esto sucede, aparece una advertencia en el registro de PHP:

```terminal
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

No hay ningún valor &quot;adecuado&quot; para `max-input-vars`; depende del tamaño y la complejidad de la configuración. Modifique el valor del archivo `php.ini` según sea necesario. Consulte [Configuración de PHP requerida](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## error de nivel máximo de anidamiento de función xdebug

Ver [Durante la instalación, error de nivel máximo de anidamiento de función xdebug](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Los errores se muestran al acceder a una plantilla PHTML

El texto de error suele ser:

```terminal
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Solución: establezca `asp_tags = off` en php.ini

Varias plantillas tienen sintaxis para admitir el nivel abstracto en plantillas (utilice distintos motores de plantillas como Twig) envueltas en `<% %>` etiquetas, como esta [plantilla](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) para mostrar una imagen de producto:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Más información sobre [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Edite `php.ini` y establezca `asp_tags = off`. Para obtener más información, consulte [Configuración de PHP requerida](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
