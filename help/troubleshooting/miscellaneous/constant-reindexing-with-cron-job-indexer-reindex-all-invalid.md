---
title: Los índices invalidados y "indexer_reindex_all_invalid" se ejecutan constantemente
description: Los índices invalidados y "indexer_reindex_all_invalid" se ejecutan constantemente
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Índices invalidados y `indexer_reindex_all_invalid` funcionar constantemente

Este artículo proporciona una posible solución al problema cuando el sitio tiene problemas de rendimiento causados por una reindexación constante. Esto se debe a que [!DNL cron] trabajo `indexer_reindex_all_invalid` ejecución continua y limpieza de cachés en [!DNL reindex].

## Productos y versiones afectados

* Adobe Commerce (nube y local) 2.4.0+ (como **[!UICONTROL Category Permissions]** es una función exclusiva de Commerce de Adobe, no afectará a Magento Open Source).

## Problema

Entrada [!DNL New Relic One] los registros de errores deben mostrar `indexer_update_all_views` se ejecuta muchas veces con un tiempo > 1 segundo (es decir, está procesando algo).

## Causa

Cuando se ejecuta el importador principal de Adobe Commerce (manualmente o por [!DNL cron]), se ejecuta un conjunto de complementos en varios módulos principales para determinar qué índices deben invalidarse.

El problema se produce cuando la variable **[!UICONTROL Category Permissions]** El módulo está habilitado en [!DNL Commerce Admin]. Si es verdadero, el complemento del módulo siempre invalida los índices de productos y categorías (y los índices vinculados) cuando se ejecuta una importación. Si se examinan los tipos de importación estándar, todos afectan a **[!UICONTROL Category Permissions]**. Se espera una invalidación.

Además, cuando un sitio tiene habilitados los módulos B2B, si **[!UICONTROL Shared Catalog]** se activa, se activa y se bloquea **[!UICONTROL Category Permissions]**. Desactivando **[!UICONTROL Shared Catalog]** se desbloqueará **[!UICONTROL Category Permissions]**, pero no desconectarlo.

<u>Comprobando [!DNL cron] inicia sesión en su [!DNL MySQL] database</u>:

Si inicia sesión en su [!DNL MySQL] base de datos, pueden comprobar su `cron` registro para **[!DNL reindex all indexes]** proceso.
Esta **debería** aparecen muchas veces, pero el factor importante es que el proceso hace una de dos cosas posibles.

El proceso solo puede hacer una de estas dos cosas:

1. Nada: tardaría de 0 a 1 segundo (un segundo o menos): el proceso comprueba si necesita hacer algo y luego se detiene si no necesita hacer nada.
1. [!DNL Reindex] todo: siempre llevará tiempo, por lo general minutos.

Normalmente, le gustaría ver muchas ocurrencias del proceso, pero con un tiempo de ejecución inferior a 1 segundo.
Por lo tanto, un comerciante puede utilizar esto [!DNL MySQL] consulta para buscar transacciones que requieren **más de 1 segundo** para ejecutar:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Puede ver cuánto tiempo se registra un periodo ejecutando:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Si esto no le proporciona un período de tiempo lo suficientemente largo como para realizar una evaluación adecuada, puede aumentar el tiempo de una prueba con éxito `cron` El proceso se mantiene en el registro siguiente a esto [[!DNL Cron] (tareas programadas)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) guía y aumento de la **[!DNL Success History Lifetime]** (el valor predeterminado es solo 60 minutos).


## Solución

Ampliar `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` para que el `afterImportSource` El método excluye el importador personalizado.

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

Donde `ENTITY_CODE` es el valor utilizado para el parámetro de nombre de entidad en `import.xml` para el importador personalizado.

## Lectura relacionada

[Configurar [!DNL cron] trabajos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) en la guía Adobe Commerce Operations Configuration Guide.
