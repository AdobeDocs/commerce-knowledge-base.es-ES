---
title: Asegúrese de que el Elasticsearch está instalado correctamente
description: Este artículo trata sobre las soluciones para problemas causados por una instalación y configuración incorrecta del Elasticsearch (ES).
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Asegúrese de que el Elasticsearch está instalado correctamente

Este artículo trata sobre las soluciones para problemas causados por una instalación y configuración incorrecta del Elasticsearch (ES).

>[!WARNING]
>
>En Adobe Commerce sobre la infraestructura en la nube, tenga en cuenta que las actualizaciones de servicios no se pueden insertar en el entorno de producción sin un aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Así que 48 horas antes de cuando sus cambios deben estar en producción, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detallando la actualización de servicio necesaria e indicando la hora en la que desea que se inicie el proceso de actualización.

## Compatibilidad de la versión del Elasticsearch con Adobe Commerce

* Adobe Commerce local y Adobe Commerce en la infraestructura en la nube:
   * v2.2.3+ es compatible con ES 5.x
   * v2.2.8+ y v2.3.1+ admiten ES 6.x
   * No se recomienda ES v2.x y v5.x debido a [Fin de vida útil](https://www.elastic.co/support/eol). Sin embargo, si tiene Adobe Commerce v2.3.1 y desea utilizar ES 2.x o ES 5.x, debe [Cambiar el Elasticsearch php Client](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html).
* Magento Open Source v2.3.0+ es compatible con ES 5.x y 6.x (pero se recomienda 6.x).

## Problema

Los siguientes síntomas indican que el Elasticsearch no está configurado correctamente:

* `Error: No alive nodes in your cluster` - este error puede aparecer en los registros de Adobe Commerce:
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * o en el indicador (por ejemplo, cuando se ejecuta una reindexación)
* Errores que indican que la versión del Elasticsearch no es compatible con su versión actual de Adobe Commerce (se trata de un error específico de Adobe Commerce en la infraestructura de la nube):

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

Donde *version* es el servicio de Elasticsearch que se ejecuta en el entorno de la nube.

## Causa

El Elasticsearch no está instalado correctamente. Esto puede deberse a lo siguiente:

* Un error tipográfico en el archivo de configuración.
* Una versión del archivo de configuración que no coincide con ninguna versión de Elasticsearch instalada para el entorno.
* Una versión que esté correctamente instalada en el entorno, correctamente configurada en el archivo de configuración, pero que no sea compatible con la versión de Adobe Commerce instalada actualmente.

## Solución

Para configurar correctamente el Elasticsearch:

* Los comerciantes de Adobe Commerce en la infraestructura en la nube pueden seguir los pasos que se indican en nuestra documentación para desarrolladores: [Configuración del servicio de Elasticsearch](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-elastic.html).
* Los comerciantes en Adobe Commerce local y los Magento Open Source pueden seguir los pasos que se indican en nuestra documentación para desarrolladores: [Elasticsearch de instalación y configuración](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

Después de configurar Elasticsearch, compruebe que esté configurado correctamente:

1. Inicie sesión en el servidor.
1. Compruebe el número de versión del Elasticsearch (2.x, 5.x o 6.x) en la salida de ejecución del comando: `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` Por ejemplo, en Adobe Commerce en la infraestructura en la nube: `curl -XGET localhost:9200`
1. Compruebe lo que está configurado en Adobe Commerce en la configuración de la infraestructura en la nube ejecutando el comando: `php bin/magento config:show catalog/search`
1. Marque `catalog/search/engine` y asegúrese de que coincida con el número de versión del Elasticsearch. Por ejemplo, en Adobe Commerce en la infraestructura en la nube:
   * Elasticsearch 5.X - elasticsearch5
   * Elasticsearch 6.X - elasticsearch6
   * Elasticsearch 2.X - elasticsearch
1. Marque `index_prefix`. Si tiene varios entornos, asegúrese de que tiene diferentes `index_prefix` valores para ellos.
