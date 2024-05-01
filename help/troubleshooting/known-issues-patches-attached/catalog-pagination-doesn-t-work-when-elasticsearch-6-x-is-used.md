---
title: La paginación del catálogo no funciona con Elasticsearch 6.x
description: Este artículo proporciona un parche para el problema de Adobe Commerce en el que la paginación del catálogo no funciona en Elasticsearch 6.x.
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# La paginación del catálogo no funciona con Elasticsearch 6.x

Este artículo proporciona un parche para el problema de Adobe Commerce en el que la paginación del catálogo no funciona en Elasticsearch 6.x.

El parche siguiente resuelve los problemas que los usuarios de Adobe Commerce 2.3.3 experimentan en implementaciones en las que Elasticsearch 6.x se utiliza como motor de búsqueda en el catálogo. Los usuarios ven un mensaje de error cuando intentan navegar más allá de la primera página de resultados de búsqueda.

Una vez instalado este parche, los usuarios podrán ver todas las páginas de los resultados de búsqueda.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.3.3
* Adobe Commerce local 2.3.3
* Magento Open Source 2.3.3
* Elasticsearch 6.x

## Problema

Se ha detectado un problema en Magento Open Source, Adobe Commerce local y Adobe Commerce en la infraestructura en la nube, donde la paginación de la página de resultados de búsqueda no funciona si cambia de página.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. Active Elasticseach 6 como motor de búsqueda en el catálogo.
1. Añada a la categoría una serie de productos que superen el límite de 1 página establecido en el Administrador. **Nota**: 12 es el número predeterminado de productos mostrados por página en Adobe Commerce 2.3.3.
1. Abra Categoría en la tienda (ya sea en la página de resultados de búsqueda o de categoría) y vaya a la página 2.

<u>Resultado esperado</u>:

Los productos deben mostrarse en la segunda página.

<u>Resultado real</u>:

**&quot;***No podemos encontrar productos que coincidan con la selección***&quot;** El mensaje se muestra en la segunda página.

## Solución

Para solucionar el problema, aplique el parche adjunto a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar problema de paginación del catálogo en el parche de Elasticsearch 6.x](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) - El parche es compatible con todas las versiones y ediciones afectadas.

>[!WARNING]
>
>El Adobe recomienda encarecidamente que se aplique el parche lo antes posible, incluso si no ha experimentado ningún síntoma.

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
