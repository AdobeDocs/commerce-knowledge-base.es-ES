---
title: No se puede instalar usando nginx
description: Este artículo proporciona una corrección para una instalación fallida de Adobe Commerce al utilizar el servidor web nginx.
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# No se puede instalar usando nginx

Este artículo proporciona una corrección para una instalación fallida de Adobe Commerce al utilizar el servidor web nginx.

## Problema

Si utiliza el servidor web nginx e intenta instalar el software de Adobe Commerce, la instalación a veces falla.

## Solución

Puede confirmar el problema mediante el siguiente error en el directorio `var/report`:

```php
NOTE: You cannot install Adobe Commerce using the Setup Wizard because the Adobe Commerce setup directory cannot be accessed.
You can install Adobe Commerce using either the command line or you must restore access to the following directory: /var/www/html/setup
If you are using the sample nginx configuration, please go to http://ce.mtf03.bcn.magento.com/setup/";i:1;s:641:"#0 /var/www/html/lib/internal/Magento/Framework/App/Http.php(213): Magento\Framework\App\Http->redirectToSetup(Object(Magento\Framework\App\Bootstrap), Object(Exception))
```

### Solución

Instale el software de Adobe Commerce mediante la [línea de comandos](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/advanced).
