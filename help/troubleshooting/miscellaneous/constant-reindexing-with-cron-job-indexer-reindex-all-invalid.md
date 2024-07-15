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

# Los índices se invalidaron y `indexer_reindex_all_invalid` se ejecutan constantemente

Este artículo proporciona una posible solución al problema cuando el sitio tiene problemas de rendimiento causados por una reindexación constante. Esto se debe a que el trabajo [!DNL cron] `indexer_reindex_all_invalid` se está ejecutando continuamente y las cachés se limpiaron en [!DNL reindex].

## Productos y versiones afectados

* Adobe Commerce (en la nube y local) 2.4.0+ (como **[!UICONTROL Category Permissions]** es una función exclusiva de Commerce de Adobe, no afectará al Magento Open Source).

## Problema

En [!DNL New Relic One], los registros de errores deberían mostrar que `indexer_update_all_views` se está ejecutando muchas veces con un tiempo > 1 segundo (es decir, está procesando algo).

## Causa

Cuando se ejecuta el importador principal de Adobe Commerce (manualmente o por [!DNL cron]), se ejecuta un conjunto de complementos en varios módulos principales para determinar qué índices deben invalidarse.

El problema se produce cuando el módulo **[!UICONTROL Category Permissions]** está habilitado en [!DNL Commerce Admin]. Si es verdadero, el complemento del módulo siempre invalida los índices de productos y categorías (y los índices vinculados) cuando se ejecuta una importación. Si se examinan los tipos de importación estándar, todos afectarán a **[!UICONTROL Category Permissions]**. Se espera una invalidación.

Además, cuando un sitio tiene habilitados los módulos B2B, si **[!UICONTROL Shared Catalog]** está activado, se activa y bloquea **[!UICONTROL Category Permissions]**. Si se desactiva **[!UICONTROL Shared Catalog]**, se desbloqueará **[!UICONTROL Category Permissions]**, pero no se desactivará.

<u>Comprobando [!DNL cron] registros en su base de datos [!DNL MySQL]</u>:

Si inicia sesión en la base de datos [!DNL MySQL], puede comprobar el registro `cron` para el proceso **[!DNL reindex all indexes]**.
Este(a) **debería** aparecer(a) muchas veces, pero el factor importante es que el proceso realiza una de las dos acciones posibles.

El proceso solo puede hacer una de estas dos cosas:

1. Nada: tardaría de 0 a 1 segundo (un segundo o menos): el proceso comprueba si necesita hacer algo y luego se detiene si no necesita hacer nada.
1. [!DNL Reindex] todo: siempre llevará tiempo, normalmente minutos.

Normalmente, le gustaría ver muchas ocurrencias del proceso, pero con un tiempo de ejecución inferior a 1 segundo.
Por lo tanto, un comerciante puede usar esta consulta [!DNL MySQL] para buscar transacciones que tarden **más de 1 segundo** en ejecutarse:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Puede ver cuánto tiempo se registra un periodo ejecutando:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Si no le concede un período de tiempo suficiente para realizar una evaluación adecuada, puede aumentar el tiempo que se conserva un proceso `cron` correcto en el registro siguiendo esta guía [[!DNL Cron] (tareas programadas)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) y aumentando el valor **[!DNL Success History Lifetime]** (el valor predeterminado es solo 60 minutos).


## Solución

Amplíe `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` para que el método `afterImportSource` excluya el importador personalizado.

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

Donde `ENTITY_CODE` es el valor utilizado para el parámetro de nombre de entidad en el archivo `import.xml` para el importador personalizado.

## Lectura relacionada

[Configurar [!DNL cron] trabajos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) en la Guía de configuración de operaciones de Adobe Commerce.
