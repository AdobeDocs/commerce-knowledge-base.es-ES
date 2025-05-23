---
title: MySQL y Elasticsearch muestran resultados diferentes
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.3 relacionado con la obtención de diferentes resultados de búsqueda para la misma consulta de búsqueda con MySQL y Elasticsearch.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL y Elasticsearch muestran resultados diferentes

>[!WARNING]
>
> [El motor de búsqueda del catálogo MySQL se eliminará en Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Debe tener el host de Elasticsearch configurado antes de instalar la versión 2.4.0. Consulte [Instalar y configurar el Elasticsearch](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/search/overview-search) en nuestra documentación para desarrolladores.

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.2.3 relacionado con la obtención de diferentes resultados de búsqueda para la misma consulta de búsqueda con MySQL y Elasticsearch.

## Problema:

Los resultados de la búsqueda en el catálogo con el mismo conjunto de filtros difieren según el motor de búsqueda utilizado, MySQL o Elasticsearch.

<u>Pasos a seguir</u> :

1. Instale y configure el Elasticsearch.
1. En la tienda, seleccione uno de los filtros.
1. Anote el número de productos coincidentes.
1. Configure la búsqueda predeterminada [MySQL](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md).
1. En la tienda, seleccione uno de los filtros.
1. Anote el número de productos coincidentes.

<u>Resultado esperado</u>:
El número de productos coincidentes es el mismo.

<u>Resultado real</u>:
El número de productos coincidentes es diferente.

## Parche

Los parches se adjuntan a este artículo. Para descargar un parche, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre de archivo necesario o haga clic en los siguientes vínculos:

[Descargar MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[Descargar MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### Versiones de Adobe Commerce compatibles:

Los parches se han creado para:

* Adobe Commerce en la infraestructura en la nube 2.2.3 (el archivo `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch`)
* Adobe Commerce en la infraestructura de nube 2.2.6 (el archivo `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch`)

El parche `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en la infraestructura en la nube 2.2.4
* Adobe Commerce en la infraestructura en la nube 2.2.5
* Adobe Commerce local 2.2.3
* Adobe Commerce local 2.2.4
* Adobe Commerce local 2.2.5

El parche `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce local 2.2.6

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte técnico para obtener instrucciones detalladas.

## Archivos adjuntos
