---
title: Elasticsearch en el solucionador de problemas de Adobe Commerce
description: Los problemas del Elasticsearch en Adobe Commerce se pueden resolver con la herramienta de resolución de problemas del Elasticsearch. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Elasticsearch en el solucionador de problemas de Adobe Commerce

Los problemas del Elasticsearch en Adobe Commerce se pueden resolver con la herramienta de resolución de problemas del Elasticsearch. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas.

>[!WARNING]
>
>En Adobe Commerce sobre la infraestructura en la nube, tenga en cuenta que las actualizaciones de servicios no se pueden insertar en el entorno de producción sin un aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Así que 48 horas antes de que sus cambios deban estar en producción [envíe un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detallando su actualización de servicio requerida e indicando la hora en que desea que comience el proceso de actualización.

## Paso 1: Comprobación de problemas del Elasticsearch {#step-1}

+++**¿Su problema podría estar relacionado con el Elasticsearch?**

Problemas del Elasticsearch indicados por mensajes de error, &quot;_No se encontraron nodos activos en su clúster&quot;,_ productos que faltan y la visualización de información de productos antiguos.

a. SÍ - Continúe con [Paso 2](#step-2).\
b. NO: vuelva a buscar términos de búsqueda relevantes en la [Base de conocimiento del Centro de ayuda de Adobe Commerce](https://support.magento.com/hc).

+++

## Paso 2: Comprobación del problema de instalación {#step-2}

+++**¿Es una nueva instalación del Elasticsearch?**

a. SÍ: [Asegúrese de que el Elasticsearch esté instalado correctamente.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) Compruebe también si está en Adobe Commerce en la infraestructura en la nube 2.3.1 o posterior. Los comerciantes que hayan actualizado a Adobe Commerce en la infraestructura en la nube (versiones 2.3.1 y posteriores) y que tengan una versión de Elasticsearch anterior a la 6.x pueden experimentar errores al realizar la implementación. Para solucionar este problema, el módulo de cliente de Elasticsearch y el servicio de Elasticsearch deben estar en las últimas versiones recomendadas. Para ver los pasos, consulte [problemas del Elasticsearch después de la actualización a Adobe Commerce en la infraestructura en la nube 2.3.1+](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. NO: compruebe el estado del clúster. Si se encuentra en un entorno de ensayo o producción Pro, ejecute este comando: `curl -m1 localhost:9200/_cluster/health?pretty`. Si se encuentra en un entorno de integración (que incluye todas las ramas de inicio), ejecute `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`. Continúe con [Paso 3](#step-3).

+++

## Paso 3: Comprobar si el clúster de Elasticsearch está disponible {#step-3}

+++**¿Recibió una respuesta del servicio?**

a. SÍ - Continúe con [Paso 4](#step-4).\
b. NO - Continúe con [Paso 9](#step-9).

+++

## Paso 4: Verificación del clúster de Elasticsearch en buen estado {#step-4}

+++**Respuesta verde?**

a. SÍ: el Elasticsearch está disponible para procesar datos y la reindexación debería funcionar. Continúe con [Paso 5](#step-5).\
b. NO: amarillo o rojo significa que hay problemas con las conexiones entre nodos y es posible que algunos datos no estén disponibles. Si es amarillo, ejecute el comando: `php bin/magento config:show catalog/search/engine` para comprobar el motor de búsqueda. Continúe con [Paso 6](#step-6). Si está en rojo, [envía un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Paso 5: Verificación del funcionamiento de la búsqueda {#step-5}

+++**Problema de búsqueda?**

Los síntomas pueden incluir ausencia de productos, categorías vacías o ausencia de actualizaciones de productos o categorías de productos no son correctos.

a. SÍ: ejecute este comando para comprobar el estado de la búsqueda en el catálogo: `php bin/magento indexer:status`. Continúe con [Paso 8](#step-8).\
b. NO - Ejecutar comando: `php bin/magento config:show catalog/search/engine`. Continúe con [Paso 6](#step-6).

+++

## Paso 6: Comprobación de ElasticSuite {#step-6}

+++**ElasticSuite en uso?**

a. SÍ: compruebe si ElasticSuite está en la versión actual ejecutando este comando: `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` Para comprobar si esta versión está depreciada o recomendada, consulte [Github: Smile-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite). Si ElasticSuite está actualizada, continúe con [Paso 10](#step-10).\
b. NO - continuar con [Paso 7](#step-7).

+++

## Paso 7: Comprobación de las herramientas ECE actualizadas {#step-7}

+++**¿Es ECE-tools la versión más reciente?**

Ejecute el comando: `php ./vendor/bin/ece-tools -V` y compruebe la versión de ECE-tools. ¿Es la [última versión de ECE-tools](https://github.com/magento/ece-tools/releases)?

a. SÍ - Continúe con [Paso 5a](#step-5).\
b. NO - Actualice ECE-tools a la versión más actual. Ejecute el comando `php bin/magento config: show catalog/search/engine` para comprobar el motor de búsqueda. Continúe con [Paso 6](#step-6).

+++

## Paso 8: Comprobación de la reindexación {#step-8}

+++**¿Está el estado de búsqueda en el catálogo en _Procesando_?**

a. SÍ: debe esperar hasta que se haya completado el procesamiento y, a continuación, comprobar si se han actualizado las categorías de productos. Si no lo han hecho, [envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Si el estado de la búsqueda en el catálogo es _Reindex requerido_ ejecutar en CLI/Terminal: `php bin/magento cron:run`. Si esto no funciona, ejecute: `php bin/magento indexer:reindex`. Si esto no resuelve el problema, [envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Paso 9: Comprobación de la configuración de yaml {#step-9}

+++¿Se ha actualizado recientemente el archivo **`.yaml`?**

a. SÍ: compruebe la configuración del Elasticsearch `.yaml` al consultar DevDocs [Configurar Elasticsearch: para habilitar el Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml).\
b. NO - [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Paso 10: Comprobación de los índices de seguimiento {#step-10}

+++**¿Hay índices de seguimiento enumerados?**

Ejecute `curl elasticsearch.internal:9200/_cat/indices` (si se encuentra en un entorno de integración que incluye todas las ramas de inicio). Si se encuentra en un entorno de ensayo o producción Pro, ejecute `curl localhost:9200/_cat/indices`. ¿Se han enumerado los índices de seguimiento? Compruebe el resultado de `_tracking_log_`.

a. SÍ: si tiene una versión de ElasticSuite anterior a la 2.8.0, se recomienda [actualizar a ElasticSuite 2.8.0 para ajustar la retención de índices de seguimiento o deshabilitar el seguimiento](https://support.magento.com/hc/en-us/articles/360035266131?). Si no puede actualizar inmediatamente, puede [crear un cron para eliminar los índices de seguimiento](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). Sin embargo, esto podría causar problemas de rendimiento. Una vez que haya actualizado a ElasticSuite 2.8.0 o eliminado los índices de seguimiento, ejecute el comando (si está en entornos de ensayo o producción Pro):`localhost:9200/_cat/allocation?v` para comprobar el espacio disponible. Si se encuentra en uno de los entornos de integración (que incluye todas las ramas de inicio) ejecute `elasticsearch.internal:9200/_cat/allocation?v`. Continúe con [Paso 11](#step-11).\
b. NO: si está en entornos de ensayo o producción Pro, ejecute `localhost:9200/_cat/allocation?v` y compruebe el espacio disponible. Si se encuentra en uno de los entornos de integración (que incluye todas las ramas de inicio) ejecute `elasticsearch.internal:9200/_cat/allocation?v`. Continúe con [Paso 11](#step-11).

+++

## Paso 11: Búsqueda de un error específico {#step-11}

+++**¿Error específico?**

Registros de Adobe Commerce y ES, extensiones y código personalizado.

a. SÍ: revise el artículo de solución de problemas del Centro de ayuda de Adobe Commerce [Asegúrese de que el Elasticsearch Elasticsearch esté instalado correctamente](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) o [se bloquee o tenga problemas de memoria insuficiente al usar el complemento ElasticSuite](https://support.magento.com/hc/en-us/articles/360035266131).\
b. NO - Continúe con [Paso 12](#step-12).

+++

## Paso 12: Comprobación del almacenamiento disponible {#step-12}

+++**Uso del almacenamiento > 85%?**

a. SÍ - Necesita aumentar el almacenamiento disponible. Consulte DevDocs[Configurar Elasticsearch: Para habilitar el Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml). A continuación, ejecute: `localhost:9200/_cat/allocation?v` (si se encuentra en entornos de ensayo o producción Pro). Si se encuentra en uno de los entornos de integración (que incluye todas las ramas de inicio) ejecute: `elasticsearch.internal:9200/_cat/allocation?v`. Continúe con [Paso 11](#step-11).\
b. NO - [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Volver al paso 1](#step-1)
