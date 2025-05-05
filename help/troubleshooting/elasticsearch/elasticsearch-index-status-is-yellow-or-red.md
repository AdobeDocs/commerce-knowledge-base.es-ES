---
title: El estado del índice del Elasticsearch es 'amarillo' o 'rojo'
description: El artículo proporciona una corrección para los casos en los que el estado del índice de Elasticsearch no es "*verde*". '*amarillo*' indica normal y '*rojo*' indica malo. El estado "amarillo" o "rojo" puede ocurrir junto con los productos que faltan o la visualización de información antigua del producto.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# El estado del índice del Elasticsearch es &#39;amarillo&#39; o &#39;rojo&#39;

>[!WARNING]
>
> [El motor de búsqueda del catálogo MySQL se eliminará en Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Debe tener el host de Elasticsearch configurado antes de instalar la versión 2.4.0. Consulte [Instalar y configurar el Elasticsearch](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/search/overview-search).

El artículo proporciona una corrección para los casos en los que el estado del índice de Elasticsearch no es &#39;*green*&#39;. &#39;*amarillo*&#39; indica normal y &#39;*rojo*&#39; indica malo. El estado &quot;amarillo&quot; o &quot;rojo&quot; puede ocurrir junto con los productos que faltan o la visualización de información antigua del producto.

## Versiones y productos afectados

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problema

El índice de búsqueda del catálogo de Elasticsearch es lento, lo que da como resultado un estado de &#39;*amarillo*&#39; o &#39;*rojo*&#39; en lugar de &#39;*verde*&#39;. También es posible que experimente cambios que faltan en el front-end.

## Causa

Puede haber varias causas potenciales. Una causa es que la instancia del Elasticsearch se quede sin espacio en disco. Otra causa son los índices duplicados.

## Solución

Cree un nuevo volcado de mysql antes de seguir estos pasos y realizarlos fuera del horario laboral para evitar que afecte potencialmente a sus clientes:

1. Cambiar temporalmente a búsqueda MySQL: habilitar búsqueda MySQL. (Nota: Recuerde volver a cambiar a Elasticsearch o puede que experimente problemas de rendimiento).
1. Para identificar índices duplicados, ejecute el siguiente comando:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. Para eliminar índices:

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. Vuelva a habilitar el Elasticsearch.
1. Ejecute un reindexado completo.
1. Compruebe el estado de los índices ejecutando el siguiente comando:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

Si estos pasos no funcionan, [envíe un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lectura relacionada

Para obtener más información, consulte la [API de estado de clúster de Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
