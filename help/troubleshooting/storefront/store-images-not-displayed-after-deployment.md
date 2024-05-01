---
title: Almacenar imágenes que no se muestran después de la implementación
description: Este artículo proporciona una solución para los casos en los que las imágenes no se muestran correctamente después de la implementación.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: c4d586ca3980acbe4f33c5f2616ef7f3051bc7d3
workflow-type: tm+mt
source-wordcount: '162'
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

Para ello, necesita la información SSH y la URL de la tienda disponibles a través de la [Consola de nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH a su proyecto que era una fuente para [volcado base datos](/help/how-to/general/create-database-dump-on-cloud.md), tal como se describe en [SSH al entorno](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) en nuestra documentación para desarrolladores.
1. Vuelva a generar la caché de imágenes ejecutando:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Pruebe las páginas de categoría a través de la dirección URL de la tienda.
