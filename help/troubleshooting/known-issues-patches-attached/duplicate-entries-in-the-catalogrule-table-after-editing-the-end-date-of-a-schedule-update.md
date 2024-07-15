---
title: Duplicar entradas en la tabla de catálogos después de editar la fecha de finalización de una actualización de programación
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.3 en el que editar la fecha u hora de finalización de una actualización de programación de reglas de precios de catálogo resulta en la adición de entradas duplicadas a la tabla "catalog_rule" y errores en el reíndice del indexador "catalog_rule product".
exl-id: e900b712-d0f5-4404-8441-64522035ce44
feature: Cache, Catalog Management, Marketing Tools
role: Developer
source-git-commit: 496151d1fe29a66d84349e4a96e7c5563a92c5c4
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Duplicar entradas en la tabla de catálogos después de editar la fecha de finalización de una actualización de programación

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.3 en el que editar la fecha u hora de finalización de una actualización de programación de reglas de precios de catálogo resulta en agregar entradas duplicadas a la tabla `catalogrule` y errores en el reíndice del indexador `catalogrule_rule` (producto de reglas de catálogo).

## Problema

Al cambiar la fecha u hora de finalización de una actualización de programación de reglas de precios de catálogo existente, se crean entradas duplicadas en la tabla de base de datos `catalogrule`. Como resultado, el reíndice `catalogrule_rule` produce el siguiente error en el registro de excepciones: *Ya existe un elemento con el mismo identificador*.

<u>Pasos a seguir</u>:

Requisitos previos: el indizador `catalogrule_rule` está establecido en el modo *[Actualizar según lo programado](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html)*.

1. En el administrador de Commerce, cree una nueva regla de precio de catálogo en **Marketing** > **Promociones** > **Regla de precio de catálogo**.
1. En la cuadrícula **Regla de precio de catálogo**, haz clic en **Editar**, programa una nueva actualización y establece **Estado** en *Activo.*
1. Haga clic en **Ver/Editar** junto a la actualización recién creada y cambie la fecha de finalización a una hora anterior.
1. Guarde la actualización.
1. Ejecute el comando reindex para el indizador `catalogrule_rule`.

<u>Resultado esperado</u>:

El indizador `catalogrule_rule` se ha reindexado correctamente. No hay entradas duplicadas en la tabla `catalogrule`.

<u>Resultado real</u>:

Reindex falla con el siguiente error: *Ya existe un elemento con el mismo Id.*, porque hay entradas duplicadas en la tabla `catalogrule`.

## Solución

Para solucionar el problema, debe aplicar el parche adjunto y eliminar las entradas duplicadas existentes. Consulte la sección [Quitar entradas duplicadas](#remove) para obtener detalles sobre cómo comprobar si existen entradas duplicadas y eliminarlas.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-10974\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-10974_EE_2.2.3_COMPOSER_v2.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce 2.2.3

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en infraestructura en la nube 2.2.1 - 2.2.5
* Adobe Commerce local 2.2.1 - 2.2.2 y 2.2.4 - 2.2.5

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones en nuestra base de conocimiento de soporte.

## Eliminar entradas duplicadas {#remove}

>[!NOTE]
>
>Asegúrese de tener una copia de seguridad reciente antes de realizar cualquier manipulación.

Siga estos pasos para localizar las entradas duplicadas y eliminarlas:

1. Ejecute la siguiente consulta para comprobar si existen entradas duplicadas en la base de datos:

   ```SQL
   SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity group by entity_id, updated_in having count(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, updated_in HAVING COUNT(*) > 1;
   ```

   Si no hay entradas duplicadas, la respuesta estará vacía y no tiene que hacer nada más. Si existen entradas duplicadas, obtendrá el nombre de tabla y `entity_id` de la entidad duplicada, como en el ejemplo siguiente:

   ![table_results1.png](assets/table_results1.png)

   Tenga en cuenta que en determinadas tablas el nombre del campo con ID de entidad será diferente de `entity_id`. Por ejemplo, en la tabla `cms_page`, sería `page_id` en lugar de `entity_id`.

1. A continuación, debe echar un vistazo más de cerca a los duplicados y comprender cuáles deben eliminarse. Utilice una consulta similar a la siguiente para ver los duplicados. Reemplace el nombre de tabla, el nombre del ID de entidad y el valor según los resultados recibidos en el paso anterior.

   ```sql
   SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
   ```

   Recibirá una lista de registros con varias columnas. Ejemplo:

   ![table_results2.png](assets/table_results2.png)

   Los valores `created_in` y `updated_in` deben seguir este patrón: el valor `created_in` de la fila actual es igual al valor `updated_in` de la fila anterior. Además, la **primera fila** debe contener created\_in = 1 y la **última fila** debe contener updated\_in = 2147483647. (Si solo hay 1 fila, debe ver created\_in=1 **and** updated\_in=2147483647). Las filas para las que se ha roto este patrón deben eliminarse. En nuestro ejemplo, sería la fila con `row_id` =2052, ya que la segunda y la tercera filas comparten el mismo valor para created_in: 1540837826, lo que no debería suceder.

1. Elimine el duplicado con una consulta similar a la siguiente. Reemplace el nombre de tabla, el nombre del ID de entidad y el valor según los resultados recibidos en los pasos anteriores:

   ```sql
   DELETE FROM catalog_product_entity WHERE entity_id = 483 AND row_id = 2052;
   ```

1. Limpie la caché ejecutando:

   ```bash
   bin/magento cache:clean
   ```

   o en el Administrador de Commerce en **Sistema** > **Herramientas** > **Administración de caché**.

## Vínculos útiles en nuestra documentación para desarrolladores

* [Aplicar parches personalizados a Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)
* [Ver y administrar registros para Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html))

## Archivos adjuntos
