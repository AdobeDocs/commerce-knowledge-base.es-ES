---
title: No se puede eliminar el origen ni cambiar su código
description: Este artículo proporciona una corrección para los casos en los que no se puede quitar completamente un origen o cambiar su código.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# No se puede eliminar el origen ni cambiar su código

Este artículo proporciona una corrección para los casos en los que no se puede quitar completamente un origen o cambiar su código.

## Problema

Las fuentes no se pueden eliminar independientemente de la asignación del producto.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube (todas las versiones), con Magento Inventory instalado
* Adobe Commerce local 2.3.0 y posterior, con Magento Inventory instalado
* Magento Open Source 2.3.0 y versiones posteriores, con Magento Inventory instalado

## Causa

Por diseño, no es posible quitar completamente un origen y/o cambiar su código.

La eliminación completa de un origen causaría problemas de datos de pedidos porque los orígenes forman parte de inventarios de productos, pedidos, datos de envíos y mucho más.

El código es vital para conectar el origen a los pedidos. Se trata de un ID único para el origen y no se puede editar.

## Solución

Puede eliminar un origen de un producto transfiriendo el inventario o soltando el producto de todos los envíos en una ubicación.

Si necesita quitar un origen de los cálculos de [SSA](https://devdocs.magento.com/guides/v2.3/inventory/source-selection-algorithms.html) y el procesamiento de pedidos de Adobe Commerce Inventory, puede deshabilitar el origen. Los orígenes desactivados conservan todos los datos, los productos asignados y las cantidades de inventario, y se pueden volver a activar en cualquier momento para comenzar a enviar de nuevo.

Consulte la [Guía de creación de fuentes](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources) para obtener más información sobre cómo deshabilitar un origen.
