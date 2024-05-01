---
title: Obtención de miles de resultados al buscar un producto en particular
description: Este artículo proporciona una solución al problema en el que obtiene miles de resultados de búsqueda cuando busca un producto en particular.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Obtención de miles de resultados al buscar un producto en particular

Este artículo proporciona una solución al problema en el que obtiene miles de resultados de búsqueda cuando busca un producto en particular.

## Productos y versiones afectados

* Adobe Commerce todas las versiones con [!DNL ElasticSearch] instalado

## Problemas

Está buscando un producto en particular (por ejemplo, *WSH12-32-Rojo*), pero la búsqueda devuelve muchos productos similares.

## Soluciones

La naturaleza de una búsqueda de texto completo en [!DNL ElasticSearch] se basa en la relevancia, no en la coincidencia exacta. Por lo tanto, las coincidencias más relevantes (como el SKU exacto coincidente) se solicitan primero.

Sin embargo, si necesita un resultado de búsqueda que coincida exactamente con el término de búsqueda (coincidencia exacta), debe utilizar comillas para la consulta de búsqueda. Por ejemplo, consulte *WSH12-32-Rojo* sin comillas devolverá varios resultados con la coincidencia exacta (producto con *SKU WSH12-32-roja*) que aparece primero en el resultado. Pero consulta citada *&quot;WSH12-32-Red&quot;* solo devolverá un resultado de coincidencia exacto.
