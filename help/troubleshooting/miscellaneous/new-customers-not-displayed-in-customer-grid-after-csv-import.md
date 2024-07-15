---
title: Los clientes nuevos no se muestran en la cuadrícula del cliente después de la importación de CSV
description: Este artículo soluciona el problema que se producía cuando no se podían ver nuevos clientes en **Clientes** &gt; **Todos los clientes** tras una importación desde un archivo ".csv". La solución es establecer el indexador customer_grid en el modo "Actualizar al guardar" y reindexar manualmente la cuadrícula del cliente.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Los clientes nuevos no se muestran en la cuadrícula del cliente después de la importación de CSV

Este artículo proporciona una solución para el problema cuando no puede ver nuevos clientes en **Clientes** > **Todos los clientes** después de una importación de un archivo de `.csv`. La solución consiste en establecer el indizador `customer_grid` en el modo &quot;Actualizar al guardar&quot; y reindexar manualmente la cuadrícula del cliente.

## Versiones afectadas

* Adobe Commerce local 2.2.0 y posterior
* Adobe Commerce en la infraestructura en la nube 2.2.0 y posterior

## Problema

Después de importar nuevos clientes desde un archivo de `.csv` mediante la funcionalidad de importación nativa de Adobe Commerce, es posible que no pueda ver los registros de nuevos clientes en **Clientes** > **Todos los clientes** en el administrador hasta que reindexe manualmente el indizador `customer_grid`.

## Causa

El modo de indización &quot;Actualización programada&quot; de Adobe Commerce 2.2.0 y versiones posteriores no admite el indizador `customer_grid` debido a problemas de rendimiento.

## Solución

Configure el indizador `customer_grid` para que se reindexe usando el modo &quot;Actualizar al guardar&quot;. Para ello, siga los siguientes pasos:

1. Inicie sesión en el administrador de Commerce.
1. Haga clic en **Sistema** > **Herramientas** > **Administración de índices**.
1. Seleccione la casilla de verificación situada junto a Indexador de cuadrícula de cliente.
1. En la lista desplegable **Acciones**, seleccione *Actualizar al guardar*.
1. Haga clic en **Enviar**.

También recomendamos reindexar manualmente el indexador `customer_grid` después de configurar el modo de indexación para garantizar que el índice esté actualizado y pueda trabajar con cron. Para reindexar manualmente, utilice el siguiente comando:

`bin/magento indexer:reindex customer_grid`

## Más información

Vínculos a temas relacionados en nuestra documentación para desarrolladores:

* [Resumen de indización](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Administrar los indexadores](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
