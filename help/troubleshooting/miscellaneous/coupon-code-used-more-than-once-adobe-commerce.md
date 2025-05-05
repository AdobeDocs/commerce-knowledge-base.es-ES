---
title: El cupón de un solo uso se utiliza varias veces, Adobe Commerce
description: Este artículo proporciona una solución para el problema cuando los cupones de la regla de precios del carro de compras no funcionan correctamente. Los comerciantes configuran un cupón para un solo uso y los clientes pueden utilizarlo varias veces.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
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

Para ver los pasos detallados, consulte [Administrar colas de mensajes > Configuración](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration) en nuestra documentación para desarrolladores.

## Lectura relacionada

[Resumen de colas de mensajes](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) en nuestra documentación para desarrolladores.
