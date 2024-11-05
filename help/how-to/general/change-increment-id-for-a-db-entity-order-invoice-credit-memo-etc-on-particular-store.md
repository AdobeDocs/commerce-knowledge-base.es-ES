---
title: Cambiar el ID de incremento de una entidad de la base de datos (pedido, factura, nota de abono, etc.) en un almacén concreto
description: En este artículo se explica cómo cambiar el ID de incremento de una entidad de la base de datos de Adobe Commerce (base de datos) (pedido, factura, nota de abono, etc.) en un almacén de Adobe Commerce concreto mediante la instrucción SQL ALTER TABLE.
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Cambiar el ID de incremento de una entidad de la base de datos (pedido, factura, nota de abono, etc.) en un almacén concreto

Este artículo explica cómo cambiar el id. de incremento de una entidad de la base de datos de Adobe Commerce (BD) (pedido, factura, nota de abono, etc.) en un almacén de Adobe Commerce concreto mediante la instrucción SQL `ALTER TABLE`.

## Versiones afectadas

* Adobe Commerce local: 2.x.x
* Adobe Commerce en infraestructura en la nube: 2.x.x
* MySQL: cualquier [versión compatible](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## ¿Cuándo tendría que cambiar el ID de incremento (casos)?

Es posible que tenga que cambiar el ID de incremento de las nuevas entidades de base de datos en estos casos:

* Después de una restauración de copia de seguridad en disco duro en un sitio activo
* Se han perdido algunos registros de pedidos, pero sus ID ya están siendo utilizados por las puertas de enlace de pago (como PayPal) para su cuenta de comerciante actual. Siendo este el caso, las puertas de enlace de pago dejan de procesar nuevos pedidos que tienen el mismo ID, devolviendo el error &quot;ID de factura duplicado&quot;

>[!NOTE]
>
>También puedes solucionar el problema de la pasarela de pago de PayPal permitiendo varios pagos por ID de factura en las Preferencias de recepción de pagos de PayPal. Ver [Solicitud rechazada de puerta de enlace de PayPal - problema de factura duplicada](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) en nuestra base de conocimiento de soporte técnico.

## Pasos previos necesarios

1. Busque tiendas y entidades para las que se debe cambiar el nuevo ID de incremento.
1. [Conéctate](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) a tu base de datos MySQL. Para Adobe Commerce en infraestructura en la nube, al principio, debes [SSH a tu entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Compruebe el valor actual auto\_increment para la tabla de secuencia de entidades mediante la siguiente consulta:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Ejemplo

Si está comprobando un incremento automático para un pedido en el almacén con *ID=1*, el nombre de tabla sería:

```sql
'sequence_order_1'
```

Si el valor de la columna `auto_increment` es *1234*, el siguiente pedido realizado en el almacén con *ID=1* tendrá el *ID \#100001234*.

### Documentación relacionada

* [Configure una conexión a base de datos MySQL remota](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) en nuestra documentación para desarrolladores.

## Actualizar entidad para cambiar el ID de incremento

Actualice la entidad con la siguiente consulta:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>Importante: El nuevo valor de incremento debe ser mayor que el actual, no menor.

### Ejemplo

Después de ejecutar la siguiente consulta:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

el siguiente pedido hecho en la tienda con *ID=1* tendrá el *ID \#100002000*.

## Pasos recomendados adicionales en el entorno de producción (nube)

Antes de ejecutar la consulta `ALTER TABLE` en el entorno de producción de Adobe Commerce en la infraestructura en la nube, se recomienda encarecidamente realizar estos pasos:

* Pruebe todo el procedimiento para cambiar el ID de incremento en el entorno de ensayo
* [Cree](/help/how-to/general/create-database-dump-on-cloud.md) una copia de seguridad de la base de datos para restaurar la base de datos de producción en caso de error

## Documentación relacionada

* [Crear volcado de base de datos en la nube](/help/how-to/general/create-database-dump-on-cloud.md) en nuestra base de conocimiento de soporte
* [SSH para su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) en nuestra documentación para desarrolladores
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
