---
title: El orden de las opciones del paquete no se actualiza mediante la importación
description: Este artículo proporciona una solución al problema cuando, después de importar productos desde un archivo .csv, las opciones de productos del paquete aparecen en un orden diferente al que se muestran en el archivo de importación.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# El orden de las opciones del paquete no se actualiza mediante la importación

Este artículo proporciona una solución al problema cuando, después de importar productos desde un archivo .csv, las opciones de productos del paquete aparecen en un orden diferente al que se muestran en el archivo de importación.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* Adobe Commerce local 2.2.x, 2.3.x
* Magento Open Source

## Problema

<u>Requisitos previos</u>:

Tiene un archivo .csv válido que contiene productos agrupados.

<u>Pasos a seguir</u>:

1. Importe el archivo utilizando la variable [Funcionalidad de importación](https://docs.magento.com/m2/ee/user_guide/system/data-import.html).
1. Abra la página del producto del paquete.

<u>Resultados esperados</u>:

El orden de las opciones es el mismo que en el archivo .csv.

<u>Resultados reales</u>:

El orden de las opciones es diferente al del archivo .csv.

## Causa

La posición de opciones no se ha declarado explícitamente.

## Solución

1. Declare una posición explícitamente para cada opción en la `position` parámetro del `bundle_values` en el archivo .csv. Para obtener instrucciones detalladas, consulte [Editar los datos del producto](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html#method-2-edit-the-product-data) en nuestra guía del usuario.
1. Repita la operación de importación.

Para obtener información general sobre la importación, consulte [Importando paquete de producto](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html) en nuestra guía del usuario.
