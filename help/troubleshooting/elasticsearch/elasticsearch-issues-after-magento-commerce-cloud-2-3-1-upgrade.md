---
title: problemas del Elasticsearch tras la actualización a Adobe Commerce cloud Infrastructure 2.3.1+
description: Este artículo analiza la corrección de problemas durante la implementación después de actualizar a Adobe Commerce en las versiones 2.3.1 o posterior de la infraestructura en la nube, si se encuentra en las versiones 2.x y 5.x de Elasticsearch.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# problemas del Elasticsearch tras la actualización a Adobe Commerce cloud Infrastructure 2.3.1+

>[!WARNING]
>
>[El motor de búsqueda del catálogo MySQL se eliminará en Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Debe tener el host de Elasticsearch configurado antes de instalar la versión 2.4.0. Consulte [Instalar y configurar el Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

>[!WARNING]
>
>Tenga en cuenta que las actualizaciones de servicio no se pueden insertar en el entorno de producción sin previo aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Así que 48 horas antes de que sus cambios deban estar en producción [envíe un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detallando su actualización de servicio requerida e indicando la hora en que desea que comience el proceso de actualización.

Este artículo analiza la corrección de problemas durante la implementación después de actualizar a Adobe Commerce en las versiones 2.3.1 o posterior de la infraestructura en la nube, si se encuentra en las versiones 2.x y 5.x de Elasticsearch.

## Productos y versiones afectados:

* Adobe Commerce en infraestructura en la nube 2.3.1+
* Elasticsearch 2.x y 5.x

## Causa

Los comerciantes que hayan actualizado a Adobe Commerce en la infraestructura en la nube (versiones 2.3.1 y posteriores) y que tengan una versión de Elasticsearch anterior a la 6.x pueden experimentar errores al realizar la implementación. Esto se debe a que las versiones de Elasticsearch 2.x y 5.x están [en desuso](https://www.elastic.co/support/eol) y ya no son compatibles con Adobe Commerce. El cliente Elasticsearch debe estar actualizado o si se ejecuta una implementación, se corre el riesgo de activar un error. Para obtener más información, consulte [Cambiar el cliente Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) en nuestra documentación para desarrolladores.

## Problema

Al implementar, verá un mensaje de error similar al siguiente, que indica que la versión del Elasticsearch no es compatible: *La versión 5.2.2 del servicio de Elasticsearch en el nivel de infraestructura no es compatible con la versión actual del módulo elasticsearch/elasticsearch (6.7.0.0) que usa la aplicación del Magento.* *Puede solucionar este problema actualizando el servicio de Elasticsearch de su infraestructura de Magento Cloud a la versión 6.x*. Otros síntomas de este problema pueden ser la falta de imágenes y problemas con los filtros en su entorno.

## Solución

>[!WARNING]
>
>Si tiene un entorno compartido, asegúrese de que los entornos de ensayo y producción estén listos para actualizarse.

Para solucionar este problema, el módulo de cliente de Elasticsearch y el servicio de Elasticsearch deben estar en las últimas versiones recomendadas:

1. Siga las instrucciones para [cambiar el módulo del Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) en nuestra documentación para desarrolladores de modo que tenga la última versión recomendada del módulo del cliente del Elasticsearch.
1. [Envíe un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) y solicite una actualización del servicio de Elasticsearch a 6.x en ensayo y producción. Tenga en cuenta que la actualización al servicio de Elasticsearch puede tardar un poco en completarse.

## Lectura relacionada

* [Requisitos de pila de tecnología Adobe Commerce 2.3](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview) en nuestra documentación para desarrolladores.
* [Configure el servicio de Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) en nuestra documentación para desarrolladores.
* [Instale y configure el Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) en nuestra documentación para desarrolladores.
* [Asegúrese de que el Elasticsearch esté instalado correctamente](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) en nuestra base de conocimiento de soporte.
