---
title: El cupón de un solo uso se utiliza varias veces, Adobe Commerce
description: Este artículo proporciona una solución para el problema cuando los cupones de la regla de precios del carro de compras no funcionan correctamente. Los comerciantes configuran un cupón para un solo uso y los clientes pueden utilizarlo varias veces.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%
---
# El cupón de un solo uso se utiliza varias veces, Adobe Commerce

Este artículo proporciona una solución para el problema cuando los cupones de la regla de precios del carro de compras no funcionan correctamente. Los comerciantes configuran un cupón para un solo uso y los clientes pueden utilizarlo varias veces.


## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.4.3 y superior

## Problema

Los comerciantes configuran un cupón para un solo uso y los clientes pueden utilizarlo varias veces.

<u>Pasos a seguir</u>:

1. Cree un cupón y configúrelo para un solo uso.
1. Continúe con el cierre de compra.
1. Utilice el cupón que acaba de crear.
1. Vuelva a cerrar la compra y utilice el mismo cupón.

<u>Resultado esperado</u>:

El cupón solo se puede utilizar una vez. Aparece un mensaje: *El código de cupón &quot;COUPON_NAME&quot; no es válido*.

<u>Resultado real</u>:

El cupón se puede utilizar más de una vez.


## Causa

Los comerciantes no han configurado y ejecutado el consumidor `sales.rule.update.coupon.usage`, lo que provoca un comportamiento incorrecto.

## Solución

Agregar el consumidor `sales.rule.update.coupon.usage` al archivo `app/etc/env.php`.

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

Para ver los pasos detallados, consulte [Administrar colas de mensajes > Configuración](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration) en nuestra documentación para desarrolladores.

## Lectura relacionada

[Resumen de colas de mensajes](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) en nuestra documentación para desarrolladores.
