---
title: Obtención de miles de resultados al buscar un producto en particular
description: Este artículo proporciona una solución al problema en el que obtiene miles de resultados de búsqueda cuando busca un producto en particular.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%
---
# Obtención de miles de resultados al buscar un producto en particular

Este artículo proporciona una solución al problema en el que obtiene miles de resultados de búsqueda cuando busca un producto en particular.

## Productos y versiones afectados

* Adobe Commerce todas las versiones con [!DNL ElasticSearch] instalado

## Problemas

Está buscando un producto en particular (por ejemplo, *WSH12-32-Red*), pero la búsqueda devuelve muchos productos similares.

## Soluciones

La naturaleza de una búsqueda de texto completo en [!DNL ElasticSearch] se basa en la relevancia, no en la coincidencia exacta. Por lo tanto, las coincidencias más relevantes (como el SKU exacto coincidente) se solicitan primero.

Sin embargo, si necesita un resultado de búsqueda que coincida exactamente con el término de búsqueda (coincidencia exacta), debe utilizar comillas para la consulta de búsqueda. Por ejemplo, la consulta de *WSH12-32-Red* sin comillas devolverá varios resultados con la coincidencia exacta (el producto con *SKU WSH12-32-Red*) que aparece primero en el resultado. Pero la consulta citada *&quot;WSH12-32-Red&quot;* solo devolverá un resultado de coincidencia exacto.
