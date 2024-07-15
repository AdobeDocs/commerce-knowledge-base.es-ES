---
title: Durante la instalación, aparece un error PDO grave
description: Este artículo proporciona una corrección para un error de DOP grave de excepción durante la instalación.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Durante la instalación, aparece un error PDO grave

Este artículo proporciona una corrección para un error de DOP grave de excepción durante la instalación.

## Problema

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## Solución

Asegúrese de instalar todas las [extensiones PHP necesarias](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html).
