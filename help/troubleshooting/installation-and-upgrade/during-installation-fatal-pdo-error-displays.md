---
title: Durante la instalación, aparece un error PDO grave
description: Este artículo proporciona una corrección para un error de DOP grave de excepción durante la instalación.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Asegúrese de instalar todas las [extensiones PHP necesarias](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings).
