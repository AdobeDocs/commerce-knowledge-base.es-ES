---
title: Problemas conocidos que afectan a la instalación de xdebug
description: Este artículo proporciona una solución para cuando experimenta un error de excepción al utilizar la extensión opcional PHP xdebug.
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Problemas conocidos que afectan a la instalación de xdebug

Este artículo proporciona una solución para cuando experimenta un error de excepción al utilizar la extensión PHP opcional `xdebug`.

* Durante la instalación
* Acceso al administrador de Commerce o a la tienda tras una instalación correcta

Excepción de ejemplo:

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

Para resolver este problema, puede:

* Deshabilite la extensión `xdebug`.
* Establezca el valor de `xdebug.max_nesting_level` en un valor de 200 o más. Para obtener más información, consulte [documentación de xdebug](http://xdebug.org/docs/basic#max_nesting_level).

Después de cambiar la configuración de o deshabilitar `xdebug`, reinicie Apache:

* CentOS: `sudo service httpd restart`
* Ubuntu: `sudo service apache2 restart`
