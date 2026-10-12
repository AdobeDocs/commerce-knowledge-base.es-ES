---
title: Problemas conocidos que afectan a la instalación de xdebug
description: Este artículo proporciona una solución para cuando experimenta un error de excepción al utilizar la extensión opcional PHP xdebug.
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '109'
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
