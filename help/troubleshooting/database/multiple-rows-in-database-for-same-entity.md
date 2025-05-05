---
title: Hay varias filas en la base de datos para la misma entidad
description: Este artículo proporciona una solución al problema de que haya varias filas para el mismo ID de entidad en la base de datos.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# Varias filas en la base de datos para la misma entidad

Este artículo proporciona una solución al problema de que haya varias filas para el mismo ID de entidad en la base de datos.

## Productos y versiones afectados:

* Adobe Commerce (todas las versiones)

## Problema

Hay varias filas para el mismo ID de entidad en la base de datos.

Por ejemplo, después de recibir una lista de registros con ID de entidad duplicados al ejecutar esta consulta:

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

Donde `$entityID = ID` de categoría/producto/regla de precio del carro/regla de precio del catálogo/página de CMS.

| Entidad | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| Categoría/Producto | catalog_category_entity/catalog_product_entity | entity_id |
| Regla de precio del carro de compras/Regla de precio del catálogo | salesrule/catalogrule | rule_id |
| Página de CMS | cms_page | page_id |

## Causa

Este es el comportamiento esperado. Las varias filas se crean mediante la funcionalidad Ensayo de contenido:

* Si especifica una fecha de inicio sin una fecha de finalización, habrá al menos dos filas con la misma entidad, regla o ID de página. Una fila indicará el estado original de la entidad (la fila en la que `created_in=1`) y una fila indicará el *Final de la actualización programada*.

* Si especifica una fecha de inicio con una fecha de finalización, habrá al menos tres filas con la misma entidad, regla o ID de página. Una fila indicará el estado original de la entidad (la fila en la que `created_in=1`), una fila será para *Inicio de la actualización programada* y una fila será para *Fin de la actualización programada*.

Por ejemplo, en esta consulta:

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* Los valores `created_in` y `updated_in` deben seguir este patrón: el valor `created_in` de la fila actual es igual al valor `updated_in` de la fila anterior. Además, la primera fila debe contener `created_in = 1` y la última fila debe contener `updated_in = 2147483647`. (Si solo hay una fila, debe ver `created_in=1` y `updated_in=2147483647`).

### ¿Por qué aparece la segunda entrada de la base de datos (y todas las siguientes) en la base de datos para la misma entidad?

* El segundo registro de la base de datos (y, posiblemente, los siguientes) para la entidad afectada significa que ha habido actualizaciones de ensayo de contenido programadas mediante el módulo `Magento_Staging`, que crea un registro adicional para una entidad en las tablas correspondientes.

Solamente se produciría un problema si los registros tienen los mismos valores para las columnas `created_in` o `updated_in`.

## Solución

Este es el comportamiento esperado y solo provocará problemas si hay discrepancias entre las filas.

## Lectura relacionada

* [Los cambios en las categorías no se están guardando](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html?lang=es) en nuestra base de conocimiento de soporte
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
