---
title: Error de procesamiento del Sistema Magento Order Management (OMS) para Adobe Commerce
description: Este artículo proporciona una solución para el problema que se produce cuando se produce un error "getMode()" en la CLI que ejecuta "bin/magento oms:messages:process" en el sistema Magento Order Management (OMS) para Adobe Commerce.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Error de procesamiento del Sistema Magento Order Management (OMS) para Adobe Commerce

Este artículo proporciona una solución para el problema que se produce cuando se produce un error de `getMode()` en la CLI que ejecuta `bin/magento oms:messages:process` en el sistema Magento Order Management (OMS) para Adobe Commerce.

## Productos y versiones afectados

Este error se produce al utilizar las versiones 3.1.1 y 3.2.0 del conector MCOM. Se resuelve en el conector MCOM 3.3.0. No es específico de una versión de MDC o MOM.

## Problema

Al ejecutar el siguiente comando en la CLI:

`bin/magento oms:messages:process`

En la CLI aparece un mensaje de error similar al siguiente:

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## Causa

Â
Esto ocurre cuando el conector intenta procesar `magento.inventory.source_management` mensajes. Connector intenta procesar estos mensajes como si fueran un mensaje de `magento.inventory.source_stock_management.update` que no requiere un valor de modo. Dado que no hay modo en los mensajes de `magento.inventory.source_mangement`, se produce el error.

## Solución

Para resolver el problema, ejecute la siguiente instrucción SQL en la CLI que elimina todos los registros de la tabla `mcom_api_messages`:

`delete from mcom_api_messages;`

## Lectura relacionada

Consulte el tutorial de configuración del conector OMS [OMS Docs](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).
