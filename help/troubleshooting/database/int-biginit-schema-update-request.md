---
title: Valor numérico de la base de datos de Adobe Commerce fuera del intervalo, de "INT" a "BIGINT"
description: Este artículo proporciona soluciones para los casos en los que no pueda guardar una actualización de producto, como un cambio de precio, o eliminar y duplicar un producto.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Valor numérico de la base de datos Adobe Commerce fuera del intervalo, `INT` a `BIGINT`

>[!WARNING]
>
>Antes de implementar la solución de este artículo (`INT` a `BIGINT` actualización de esquema), los comerciantes siempre deben comprobar que el campo que van a cambiar NO tiene ninguna relación de clave externa con otra tabla. Si el campo tiene relaciones de clave externa con otra tabla, habrá problemas porque el campo relacionado sigue siendo `INT`. Pueden utilizar la siguiente consulta para verificarlo. Esta consulta enumera las relaciones de clave externa disponibles en la base de datos para el campo de tabla dado:
>
>```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Este artículo proporciona soluciones para los casos en los que no pueda guardar una actualización de producto, como un cambio de precio, o eliminar y duplicar un producto.
Puede ver el mensaje de error *No se pudo guardar el elemento de stock. Inténtelo de nuevo.* Es posible que no pueda implementar después de una actualización de producto. También puede ver el siguiente mensaje de error de [!DNL MySQL] al ejecutar `php bin/magento setup:upgrade` (en Adobe Commerce en la infraestructura de la nube, este error se muestra en los registros de implementación):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

Las soluciones descritas en el artículo son las siguientes:
* Actualizar `[ AUTO_INCREMENT ]` al siguiente valor de la tabla o
* Actualización del esquema de `INT` a `BIGINT`

La solución que utilice depende de la causa del problema. Consulte los pasos a continuación para aislar la causa.

## Pasos para comprobar la causa


Compruebe el valor más alto de la clave principal ejecutando el siguiente comando en el terminal: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Si `max(value_id)` es menor que `max int(11) [ 4294967296 ]` y `[ AUTO_INCREMENT ]` tiene un valor mayor o igual que `max int(11) [ 4294967296 ]`, considere [actualizar `[ AUTO_INCREMENT ]` al siguiente valor de la tabla](#update-the-auto-increment-to-the-next-value-from-the-table). De lo contrario, considere una actualización de esquema [`INT` a `BIGINT`](#int_to_bigint_schema_update).

## Actualizar `AUTO_INCREMENT` al siguiente valor de la tabla {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Realice una copia de seguridad de la base de datos antes de modificar las tablas. Además, ponga el sitio en [modo de mantenimiento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=es#maintenance-mode). Además, también se recomienda ejecutar el comando optimizado [!DNL MySQL] en las tablas de base de datos (solo en las tablas en las que se han realizado cambios) después de realizar los cambios.

>[!NOTE]
>
>El sitio debe estar en modo de mantenimiento mientras se ejecuta el comando de optimización en tablas específicas. Esto reconstruye completamente las tablas y libera espacio después de eliminar los datos de las tablas.

Si el valor mostrado es menor que `max int(11) [ 4294967296 ]`, como se muestra en el siguiente ejemplo de salida de terminal, entonces una tabla `[ AUTO_INCREMENT ]` ha cambiado a un número mayor o igual que el valor `max [ int(11) ]`.

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

Para comprobar si esto ha ocurrido, ejecute el siguiente comando en el terminal:

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

Como puede ver en el resultado del ejemplo anterior, la tabla `[ AUTO_INCREMENT ]` ha cambiado a un número mayor que `max int(11) [ 4294967296 ]`. La solución consiste en actualizar `[ AUTO_INCREMENT]` al siguiente valor de la tabla:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## Actualización del esquema de `INT` a `BIGINT` {#int_to_bigint_schema_update}

Sin embargo, si al ejecutar la siguiente consulta `SELECT MAX(value_id) FROM catalog_product_entity_int;` el valor mostrado es mayor que `max int(11) [ 4294967296 ]`, considere la posibilidad de realizar una actualización de esquema de `INT` a `BIGINT`. El tipo de datos `BIGINT` tiene un rango de valores mayor.

Para ello:

1. Cree un módulo personalizado dentro del directorio *app/code/*.
1. En el módulo personalizado, cree un *db_schema.xml*. En *db_schema.xml*, establecerá el tipo de datos en `BIGINT`.
1. Agregue el siguiente contenido y luego ejecute `bin/magento setup:upgrade` para aplicar los cambios anteriores a la tabla correspondiente.

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## Lectura relacionada

* [Directrices generales [!DNL MySQL] 2&rbrace; en la Guía de instalación de Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html?lang=es)
* [La carga de la base de datos pierde la conexión con [!DNL MySQL]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html?lang=es) en nuestra base de conocimiento de soporte
* [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html?lang=es) en nuestra base de conocimiento de soporte
* [Problemas más comunes de las bases de datos en Adobe Commerce sobre la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html?lang=es) en nuestra base de conocimiento de asistencia
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
