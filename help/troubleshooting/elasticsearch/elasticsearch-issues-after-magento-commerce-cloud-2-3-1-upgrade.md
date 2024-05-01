---
title: problemas del Elasticsearch tras la actualización a Adobe Commerce cloud Infrastructure 2.3.1+
description: Este artículo analiza la corrección de problemas durante la implementación después de actualizar a Adobe Commerce en las versiones 2.3.1 o posterior de la infraestructura en la nube, si se encuentra en las versiones 2.x y 5.x de Elasticsearch.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# problemas del Elasticsearch tras la actualización a Adobe Commerce cloud Infrastructure 2.3.1+

>[!WARNING]
>
>[El motor de búsqueda del catálogo MySQL se eliminará en Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Debe tener el host de Elasticsearch configurado antes de instalar la versión 2.4.0. Consulte [Elasticsearch de instalación y configuración](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

>[!WARNING]
>
>Tenga en cuenta que las actualizaciones de servicio no se pueden insertar en el entorno de producción sin previo aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Así que 48 horas antes de cuando sus cambios deben estar en producción [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detallando la actualización de servicio necesaria e indicando la hora en la que desea que se inicie el proceso de actualización.

Este artículo analiza la corrección de problemas durante la implementación después de actualizar a Adobe Commerce en las versiones 2.3.1 o posterior de la infraestructura en la nube, si se encuentra en las versiones 2.x y 5.x de Elasticsearch.

## Productos y versiones afectados:

* Adobe Commerce en infraestructura en la nube 2.3.1+
* Elasticsearch 2.x y 5.x

## Causa

Los comerciantes que hayan actualizado a Adobe Commerce en la infraestructura en la nube (versiones 2.3.1 y posteriores) y que tengan una versión de Elasticsearch anterior a la 6.x pueden experimentar errores al realizar la implementación. Esto se debe a que las versiones de Elasticsearch 2.x y 5.x son [Fin de vida útil](https://www.elastic.co/support/eol) y ya no son compatibles con Adobe Commerce. El cliente Elasticsearch debe estar actualizado o si se ejecuta una implementación, se corre el riesgo de activar un error. Para obtener más información, consulte [Cambio del cliente Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) en nuestra documentación para desarrolladores.

## Problema

Al implementar, verá un mensaje de error similar al siguiente, que indica que la versión del Elasticsearch no es compatible: *La versión 5.2.2 del servicio de Elasticsearch en el nivel de infraestructura no es compatible con la versión actual del módulo elasticsearch/elasticsearch (6.7.0.0) que utiliza la aplicación de Magento.*  *Para solucionar este problema, actualice el servicio de Elasticsearch en su infraestructura de Magento Cloud a la versión 6.x*. Otros síntomas de este problema pueden ser la falta de imágenes y problemas con los filtros en su entorno.

## Solución

>[!WARNING]
>
>Si tiene un entorno compartido, asegúrese de que los entornos de ensayo y producción estén listos para actualizarse.

Para solucionar este problema, el módulo de cliente de Elasticsearch y el servicio de Elasticsearch deben estar en las últimas versiones recomendadas:

1. Siga las instrucciones de [cambio del módulo Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) en nuestra documentación para desarrolladores, para que tenga la última versión recomendada del módulo de cliente de Elasticsearch.
1. [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) y solicitar una actualización del servicio de Elasticsearch a 6.x en ensayo y producción. Tenga en cuenta que la actualización al servicio de Elasticsearch puede tardar un poco en completarse.

## Lectura relacionada

* [Requisitos de pila de tecnología Adobe Commerce 2.3](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements-tech.html) en nuestra documentación para desarrolladores.
* [Configuración del servicio de Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html) en nuestra documentación para desarrolladores.
* [Elasticsearch de instalación y configuración](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) en nuestra documentación para desarrolladores.
* [Asegúrese de que el Elasticsearch está instalado correctamente](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) en nuestra base de conocimiento de soporte.
