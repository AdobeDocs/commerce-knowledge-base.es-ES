---
title: Bootstrap Adobe Commerce 2 en un script de zona protegida
description: "Para inicializar una aplicación de Adobe Commerce 2 en un script de zona protegida de ejemplo, ejecute el siguiente script desde el directorio raíz de Adobe Commerce:"
exl-id: a6acb30a-5175-42c6-8de3-e80c9ae8dac1
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# Bootstrap Adobe Commerce 2 en un script de zona protegida

Para inicializar una aplicación de Adobe Commerce 2 en un script de zona protegida de ejemplo, ejecute el siguiente script desde el directorio raíz de Adobe Commerce:

```php
<?php

error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', 1);

require __DIR__ . '/app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
$objectManager = $bootstrap->getObjectManager();

//$model = $objectManager->get('Vendor\Module\Some\Model');
```
