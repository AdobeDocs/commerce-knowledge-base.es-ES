---
title: La búsqueda de coincidencia exacta no funciona en Adobe Commerce 2.4.x
description: Este artículo proporciona una aclaración para el problema en el que los resultados de búsqueda de la tienda front que utilizan la misma cadena de búsqueda difieren en Adobe Commerce 2.4.x en comparación con Adobe Commerce 2.3.x.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# La búsqueda de coincidencia exacta no funciona en Adobe Commerce 2.4.x

Este artículo proporciona una aclaración para el problema en el que los resultados de búsqueda de la tienda front que utilizan la misma cadena de búsqueda difieren en Adobe Commerce 2.4.x en comparación con Adobe Commerce 2.3.x.

## Productos y versiones afectados

- Adobe Commerce (todos los métodos de implementación) 2.4.x, 2.3.x
- Live Search

## Problema

<u>Requisitos previos:</u>

Tiene productos con valores de atributo `Saga 1` y `Saga 16` en las tiendas Adobe Commerce 2.3 y Adobe Commerce 2.4.

<u>Pasos a seguir:</u>

1. En la tienda de una tienda con tecnología Adobe Commerce 2.3, escribe *Saga 1* en el campo de búsqueda y haz clic en **Buscar**.
1. Observe que en los resultados de búsqueda sólo se obtienen los productos con el valor de atributo `Saga 1`.
1. En la tienda de una tienda con tecnología Adobe Commerce 2.4, escribe *Saga 1* en el campo de búsqueda y haz clic en **Buscar**.

<u>Resultado real:</u>

Los resultados de búsqueda en 2.4 incluyen productos con valores de atributo `Saga 1` y `Saga 16`.

<u>Resultado esperado:</u>

Los resultados de búsqueda en 2.4 son similares a 2.3 y solo incluyen productos con valor de atributo `Saga 1`.

## Causa

La funcionalidad de búsqueda nativa de Adobe Commerce utilizada en 2.3.x proporciona resultados de búsqueda de coincidencia exactos. Mientras que Live Search, un módulo opcional disponible para la instalación, que se publicó con Adobe Commerce 2.4.x, se implementa de forma diferente, y el resultado real es el comportamiento esperado cuando se utiliza el módulo.

## Lectura relacionada

[Instalar Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) en nuestra guía del usuario.

[Live Search](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search) en nuestra documentación para desarrolladores.
