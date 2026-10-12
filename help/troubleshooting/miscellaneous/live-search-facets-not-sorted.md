---
title: Las facetas [!DNL Live Search] no están ordenadas alfabéticamente
description: Este artículo proporciona información de solución de problemas si las facetas [!DNL Live Search] no están ordenadas alfabéticamente.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: 59f86727-c2a6-4418-8753-40f7937e059c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%
---
# Las facetas [!DNL Live Search] no están ordenadas alfabéticamente

## Productos y versiones afectados

Adobe Commerce versiones 2.4.x y posteriores

## Problema

Todas las facetas de tienda de Adobe Commerce se ordenan alfabéticamente con opciones de selección única, independientemente del tipo de entrada asignado al atributo correspondiente.

## Solución

Sin embargo, en algunos casos extremos, es posible que las facetas no se ordenen alfabéticamente según lo configurado en el [[!DNL Live Search] espacio de trabajo de facetas](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace).

Como solución alternativa, puede ordenar los atributos de producto en la sección de atributos [!UICONTROL Admin].

1. En la barra lateral **[!UICONTROL Admin]**, ve a **Tiendas** > *Atributos* > **Producto**.
1. Seleccione un atributo de la tabla.

   ![Lista de atributos](assets/attribute-list.png)

1. Abra el atributo que tiene los valores que desea ordenar y seleccione **Información del atributo** > **Propiedades**.
1. En **Administrar opciones**, puede ordenar los valores de atributo.

   ![Ordenar atributos](assets/sort-attributes.png)
