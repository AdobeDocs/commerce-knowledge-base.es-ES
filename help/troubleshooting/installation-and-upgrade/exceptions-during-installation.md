---
title: Excepciones durante la instalación
description: Este artículo proporciona una posible solución a los problemas relacionados con la instalación de Adobe Commerce mediante el Asistente para instalación web.
exl-id: f9b8ba2d-c8bd-4020-9e95-7194cc51317c
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Excepciones durante la instalación

Este artículo proporciona una posible solución a los problemas relacionados con la instalación de Adobe Commerce mediante el Asistente para instalación web.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problema

Se muestran excepciones durante la instalación. Los usuarios han informado de varias excepciones, entre ellas las siguientes:

```bash
Module 'Magento_Indexer':
Running recurring..
[ERROR] exception 'Exception' with message 'Recoverable Error: Argument 1 passed to Magento\Indexer\Model\Config\Data::__construct() must be an instance of Magento\Framework\Indexer\Config\Reader, instance of Magento\Indexer\Model\Config\Reader given, called in /home/magento2_dev/
public_html/generated/code/Magento/Indexer/Model/Config/Data/Interceptor.php on line 14 and defined in /home/magento2_dev/public_html/
app/code/Magento/Indexer/Model/Config/Data.php on line 22' in /home/magento2_dev/public_html/lib/internal/Magento/Framework/App/ErrorHandler.php:67
Stack trace:
#0 /home/magento2_dev/public_html/app/code/Magento/Indexer/Model/Config/Data.php(22): Magento\Framework\App\ErrorHandler->handler(4096,
'Argument 1 pass...', '/home/magento2...', 22, Array)
#1 /home/magento2_dev/public_html/generated/code/Magento/Indexer/Model/Config/Data/Interceptor.php(14): Magento\Indexer\Model\Config\Data->
__construct(Object(Magento\Indexer\Model\Config\Reader), Object(Magento\Framework\App\Cache\Type\Config), Object(Magento\Indexer\Model\Resource\Indexer\State\Collection), 'indexer_config')
#2 /home/magento2_dev/public_html/lib/internal/Magento/Framework/ObjectManager/Factory/AbstractFactory.php(103): Magento\Indexer\Model\Config\Data\Interceptor->__construct(Object(Magento\Indexer\Model\Config\Reader), Object(Magento\Framework\App\Cache\Type\Config),
Object(Magento\Indexer\Model\Resource\Indexer\State\Collection), 'indexer_config')

... more ...
```

## Solución

Borre la `<magento_root>/generated/code` y otros directorios en `var` y `generated` como sigue:

```bash
rm -rf <magento_root>/generated/code/* <magento_root>/generated/metadata/* <magento_root>/var/cache/*
```

Después de borrar los directorios, vuelva a intentar la instalación.
