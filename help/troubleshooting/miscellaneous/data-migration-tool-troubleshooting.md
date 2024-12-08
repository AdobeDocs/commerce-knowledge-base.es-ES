---
title: Herramienta de migración de datos
description: Este artículo proporciona soluciones para los errores que pueden producirse al ejecutar la herramienta de migración de datos.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 958067830d32b1f10ffa669307ec76d1e14b82a4
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Herramienta de migración de datos

Este artículo proporciona soluciones para los errores que pueden producirse al ejecutar la herramienta de migración de datos.

## Documentos/campos de Source no asignados {#source-documents-fields-not-mapped}

### Mensajes de error

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

En casos excepcionales, el mensaje puede mencionar

```bash
Destination documents
```

o

```bash
Destination fields
```

en lugar de los de origen.

### Causa

Algunas entidades de la versión 1 de Adobe Commerce (en la mayoría de los casos, procedentes de extensiones) no existen en la base de datos de la versión 2 de Adobe Commerce.

Este mensaje aparece porque la herramienta de migración de datos ejecuta pruebas internas para comprobar que las tablas y los campos son coherentes entre las bases de datos *source* (Adobe Commerce 1) y *destination* (Adobe Commerce 2).

### Posibles soluciones

* Instale las extensiones de Adobe Commerce 2 correspondientes desde [Commerce Marketplace](https://marketplace.magento.com/).     Si los datos en conflicto se originan en una extensión que agrega propios elementos de estructura de base de datos, la versión de Adobe Commerce 2 de la misma extensión puede agregar dichos elementos a la base de datos de destino (Adobe Commerce 2), lo que soluciona el problema.
* Utilice el argumento `-a` al ejecutar la herramienta para resolver automáticamente los errores y evitar que se detenga la migración.
* Configure la herramienta para ignorar los datos problemáticos.

Para omitir entidades de base de datos, agregue la etiqueta `<ignore>` a una entidad del archivo `map.xml` de la siguiente manera:

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>Antes de ignorar entidades por archivo de asignación o utilizando la opción `-a`, asegúrese de que no necesita los datos afectados en su tienda de Adobe Commerce 2.

## La clase no está asignada en el registro {#class-does-not-exist-but-mentioned}

### Mensaje de error

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Causa

No se pudo encontrar una clase del código base de Adobe Commerce 1 en el código base de Adobe Commerce 2 durante el [paso de migración EAV](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/data-migration/basics/technical-specification) en nuestra documentación para desarrolladores. En la mayoría de los casos, la clase que falta pertenece a una [extensión](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/glossary#extension).

### Posibles soluciones

* Instale la extensión de Adobe Commerce 2 correspondiente.
* Ignore el atributo que causa el problema.    Para ello, agregue el atributo al grupo `ignore` en el archivo `eav-attribute-groups.xml.dist`.
* Agregue la asignación de clase mediante el archivo `class-map.xml.dist`.

## Error de restricción de clave externa

### Texto del mensaje de error

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Causa

Faltan registros de base de datos en el `parent_table` al que señala el `field_id` del `child_table`.

### Posible solución

Elimine los registros de `child_table` si no los necesita.

Para conservar los registros, deshabilite `Data Integrity Step` modificando `config.xml` de la herramienta de migración de datos

## Duplicados en reescrituras de URL

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Causa

`Target path` en una reescritura de URL debe estar especificado por un par único de `Request path` + `Store ID` Este error informa de dos entradas que utilizan el mismo par `Request path` + `Store ID` con dos valores `Target path` diferentes.

### Posible solución

Habilite la opción `auto_resolve_urlrewrite_duplicates` en el archivo `config.xml`.

Esta configuración agrega una cadena hash a los registros en conflicto de las reescrituras de URL y muestra el resultado de la resolución en la interfaz de línea de comandos.

## Discrepancia de entidades {#mismatch-of-entities}

### Mensaje de error

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Causa

El error se produce durante el paso de comprobación de volumen. Significa que el recuento de registros de la base de datos Adobe Commerce 2 del documento no es el mismo que en Adobe Commerce 1.

Los registros que faltan se producen cuando un cliente realiza un pedido durante la migración.

### Posible solución

Ejecute la herramienta de migración de datos en el modo `Delta` para transferir los cambios incrementales.

## Deltalog no está instalado {#deltalog-is-not-installed}

### Mensaje de error

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Causa

Este error se produce durante la [migración incremental](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/data-migration/migrate-data/delta) (en nuestra documentación para desarrolladores) de cambios en los datos. Significa que no se encontraron tablas deltalog (con prefijo `m2_cl_*`) en la base de datos de Adobe Commerce 1. La herramienta instala estas tablas durante la [migración de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/data-migration/migrate-data/data) (en nuestra documentación para desarrolladores), así como los déclencheur de la base de datos que realizan un seguimiento de los cambios y rellenan las tablas de cuadros de diálogo.

Una de las razones del error podría ser que está intentando migrar desde una *copia* de su tienda Adobe Commerce 1 activa, no desde la propia tienda Live. Cuando se realiza una copia desde un almacén de Adobe Commerce 1 activo que nunca se ha migrado, la copia no contiene los déclencheur ni las tablas de deltalog adicionales necesarias para completar una migración de delta, por lo que la migración falla. La herramienta de migración de datos NO realiza comparaciones entre las bases de datos de AC1 y AC2 para migrar las diferencias. En su lugar, la herramienta utiliza los déclencheur y las tablas de deltalog instalados durante la primera migración para realizar migraciones delta posteriores. En tal caso, la copia de la base de datos de Adobe Commerce 1 activa no contendrá los déclencheur ni las tablas de cuadros de diálogo de deltalog que la herramienta de migración de datos utiliza para realizar una migración.

### Posible solución

Se recomienda probar el proceso de migración desde una copia de la base de datos de Adobe Commerce 1 para solucionar los problemas de migración. Después de corregir los problemas en la copia, inicie el proceso de migración de nuevo desde la base de datos de Adobe Commerce 1 activa. Esto ayudará a garantizar un proceso de migración sin problemas.

## Lectura relacionada

[Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

