---
title: El envío directo recoge una dirección incorrecta
description: La solución de envío no recoge la dirección del origen del producto.
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# El envío directo recoge una dirección incorrecta

## Problema

La solución de envío no recoge la dirección del origen del producto.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube (todas las versiones), con Magento Inventory instalado
* Adobe Commerce local 2.3.0 y posterior, con Magento Inventory instalado
* Magento Open Source 2.3.0 y versiones posteriores, con Magento Inventory instalado

### Causa

Magento Inventory no admite actualmente el uso del cálculo de tarifas de envío directo basadas en la dirección de origen durante el cierre de compra. En su lugar, se utiliza la dirección de almacén predeterminada de la configuración en todos los casos.

## Lectura relacionada

* [Preguntas frecuentes sobre inventario de Magento](https://github.com/magento/inventory/wiki/MSI-FAQs) en GitHub.
