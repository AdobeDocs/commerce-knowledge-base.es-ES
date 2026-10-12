---
title: Almacenar imágenes que no se muestran después de la implementación
description: Este artículo proporciona una solución para los casos en los que las imágenes no se muestran correctamente después de la implementación.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%
---
# Almacenar imágenes que no se muestran después de la implementación

Este artículo proporciona una solución para los casos en los que las imágenes no se muestran correctamente después de la implementación.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x

## Problema

Cuando se utiliza una temática de tienda con cambio de tamaño de imagen, las imágenes no se muestran ni desaparecen de las páginas del catálogo cuando se implementan.

## Causa

Esto puede ocurrir debido a la carga de las imágenes de la caché.

## Solución

Si esto sucede, puede utilizar el comando Magento para regenerar la caché de imágenes y mostrar correctamente las imágenes.

Para ello, necesita la información SSH y la URL del almacén disponibles a través de [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=es).

1. SSH para su proyecto que era una fuente para el [volcado de la base de datos](/help/how-to/general/create-database-dump-on-cloud.md), tal como se describe en [SSH para el entorno](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/secure-connections) en nuestra documentación para desarrolladores.
1. Vuelva a generar la caché de imágenes ejecutando:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Pruebe las páginas de categoría a través de la dirección URL de la tienda.
