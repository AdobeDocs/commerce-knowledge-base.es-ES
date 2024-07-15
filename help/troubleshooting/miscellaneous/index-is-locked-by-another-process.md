---
title: El índice está bloqueado por otro proceso
description: Este artículo trata sobre un problema común de indexación en Adobe Commerce en el que el índice está bloqueado por otro proceso y se omite.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# El índice está bloqueado por otro proceso

Este artículo trata sobre un problema común de indexación en Adobe Commerce en el que el índice está bloqueado por otro proceso y se omite.

## Productos y versiones afectados

* Adobe Commerce 2.X

## Problema

Durante una reindexación completa en su CLI, Adobe Commerce le muestra el mensaje de error: El índice de *está bloqueado por otro proceso de reindexación. Omitiendo.&#39;* En otras palabras, cuando el proceso o el tipo de índice están bloqueados, no se puede reindexar ese tipo de índice bloqueado en particular. El reíndice siempre omitirá ese tipo de índice.

## Causa

Este error se puede producir si el índice anterior no se completó correctamente. Algunas razones posibles son:

* Otro proceso o usuario ha interrumpido el proceso.
* Límite de memoria.
* Error de MySQL, como un tiempo de espera.
* Error grave de PHP durante la reindexación.

## Pasos a seguir

1. Por ejemplo, diga que la variable    ```bash    cataloginventory_stock ```    el tipo de índice está bloqueado.
1. Cuando intente reindexar todos los datos ejecutando el comando CLI    ```bash    php bin/magento indexer:reindex    ```, obtendrá el siguiente resultado de salida:    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. Como puede ver más arriba, la    ```bash    cataloginventory_stock```    se ha omitido el proceso de indexación.


## Solución

Debe restablecer el estado del índice e intentar ejecutar el nuevo proceso de reindexación. Para el estado del índice de restablecimiento, debe ejecutar el comando:

```bash
bin/magento indexer:reset <index identifier>
```

Si no está seguro de cuáles son los identificadores de índice (código), puede enumerarlos con el comando:

```bash
bin/magento indexer:info
```

Para completar, aquí están todas las combinaciones posibles para índices nativos:

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## Lectura relacionada

En nuestra base de conocimiento de soporte:

* [Las tareas cron bloquean tareas de otros grupos (Adobe Commerce en la infraestructura en la nube)](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

En nuestra guía del usuario:

* [Administración de índices](https://docs.magento.com/user-guide/system/index-management.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

En nuestra documentación para desarrolladores:

* [Información general de indización](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Prácticas recomendadas de indizadores](https://devdocs.magento.com/guides/v2.3/performance-best-practices/configuration.html#indexers)
* [Configurar Y Ejecutar Cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html)
* [Administrar Los Indexadores](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
* [Optimización del indizador](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexer-batch.html)
