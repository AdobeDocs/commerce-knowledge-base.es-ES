---
title: Los índices de seguimiento de ElasticSuite causan problemas con Elasticsearch
description: Este artículo habla sobre el problema de los problemas de memoria Elasticsearch causados por los índices de seguimiento producidos por el complemento ElasticSuite.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Los índices de seguimiento de ElasticSuite causan problemas con Elasticsearch

>[!NOTE]
>
>ElasticSuite y sus aplicaciones afiliadas son herramientas de terceros que actualmente no son compatibles con Adobe. Este contenido se presenta solo como información y no como indicación de lo que está habilitado para la cobertura de soporte.

Este artículo habla sobre el problema de los problemas de memoria Elasticsearch causados por los índices de seguimiento producidos por el complemento ElasticSuite.

## Productos y versiones afectados

Las versiones de ElasticSuite anteriores a la 2.8.0 no pueden limpiar periódicamente los índices de seguimiento.

Las versiones de ElasticSuite anteriores a 2.9.8 / 2.10.7 almacenan índices de seguimiento en índices diarios, lo que hace que el número de índices abiertos crezca.

## Problema

Si se instala el complemento de terceros ElasticSuite, es posible que experimente problemas de memoria del Elasticsearch y que el servicio del Elasticsearch se bloquee debido a los índices de seguimiento de ElasticSuite. Los síntomas incluyen:

* El Elasticsearch se bloquea sin errores de memoria.
* Al ejecutar un comando de mantenimiento `curl -m1 localhost:9200/_cluster/health?pretty` o `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` (para cuentas de inicio) hay cientos o miles de `unassigned_shards`
* El rendimiento del Elasticsearch o del sitio está gravemente degradado.
* *&quot;No se encontraron nodos activos en su clúster&quot;* en la implementación del Elasticsearch o en los errores de registro.
* *&quot;Rechazando actualización de asignación a [&lt;\*>_ tracking_log_event _&lt;\*>]&quot;* en errores de implementación o registro.

## Causa

ElasticSuite tiene una nueva función que crea índices de seguimiento. Estos índices de seguimiento registran qué términos de búsqueda son los más utilizados, qué términos generan la mayor rotación y qué términos conducen a una página sin resultados para que los comerciantes puedan crear sinónimos para corregirlos. No parece eliminar los índices de seguimiento, por lo que Elasticsearch se queda sin recursos y se bloquea.

## Solución

### Actualice su versión de ElasticSuite para poder limpiar los índices de seguimiento periódicamente

Una vez que haya actualizado el complemento ElasticSuite a una versión superior a la 2.8.0, puede configurar una limpieza periódica de los índices.

Vaya a **Tiendas** > **Configuración** > **Seguimiento** > **Configuración global** > **Demora de retención**

El período de retención predeterminado es de 365 días. Puede reducirlo a 30 o 15 días.

### Actualice su versión de ElasticSuite para utilizar índices basados mensuales en lugar de índices basados diarios

Una vez que haya actualizado el complemento ElasticSuite a la versión > 2.9.8 / 2.10.7, los índices de seguimiento se basarán mensualmente.

Aún puede reducir el periodo de retención:

Vaya a **Tiendas** > **Configuración** > **Seguimiento** > **Configuración global** > **Demora de retención**

El periodo de retención predeterminado es de 12 meses (generará 12 índices). Puede reducirlo a 3 o 6 meses.

### Uso de un cronjob para limpiar los datos de índices de seguimiento

Cree un trabajo cron para eliminar los índices de seguimiento. Este comando elimina los índices creados en el último mes:

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

Si desea eliminar índices en una frecuencia de tiempo establecida, cree un trabajo cron consultando los siguientes artículos en nuestra documentación para desarrolladores:

* [Configurar un trabajo cron personalizado y un grupo cron (tutorial)](https://devdocs.magento.com/guides/v2.3/config-guide/cron/custom-cron-tut.html)
* [Configurar trabajos cron](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html)
