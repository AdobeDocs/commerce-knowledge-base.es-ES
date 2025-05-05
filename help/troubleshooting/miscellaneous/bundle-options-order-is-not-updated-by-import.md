---
title: El orden de las opciones del paquete no se actualiza mediante la importación
description: Este artículo proporciona una solución al problema cuando, después de importar productos desde un archivo .csv, las opciones de productos del paquete aparecen en un orden diferente al que se muestran en el archivo de importación.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Importe el archivo con la [funcionalidad de importación](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/data-transfer/import/data-import).
1. Abra la página del producto del paquete.

<u>Resultados esperados</u>:

El orden de las opciones es el mismo que en el archivo .csv.

<u>Resultados reales</u>:

El orden de las opciones es diferente al del archivo .csv.

## Causa

La posición de opciones no se ha declarado explícitamente.

## Solución

1. Declare una posición explícitamente para cada opción en el parámetro `position` de la columna `bundle_values` del archivo .csv. Para obtener instrucciones detalladas, consulte [Editar los datos del producto](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products#method-2-edit-the-product-data) en nuestra guía del usuario.
1. Repita la operación de importación.

Para obtener información general sobre la importación, consulte [Importación del producto del paquete](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products) en nuestra guía del usuario.
