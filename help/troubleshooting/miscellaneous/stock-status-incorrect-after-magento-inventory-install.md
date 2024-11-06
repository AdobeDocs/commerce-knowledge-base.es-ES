---
title: Estado de stock incorrecto tras la instalación de Inventory management
description: Este artículo proporciona una corrección para el estado de las existencias incorrecto después de la instalación/actualización de Inventory management.
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Estado de stock incorrecto tras la instalación de Inventory management

Este artículo proporciona una corrección para el estado de las existencias incorrecto después de la instalación/actualización de Inventory management.

## Estado de stock incorrecto en algunos sitios

Después de instalar o actualizar por primera vez para que Inventory management esté en el entorno de Adobe Commerce de varios sitios web, no todos los sitios web tienen los estados de existencias correctos para los productos.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones, con Inventory management instalado
* Adobe Commerce local 2.3.0 y posterior, con Inventory management instalado
* Magento Open Source 2.3.0 y versiones posteriores, con Inventory management instalado

## Causa

Al instalar o actualizar por primera vez, todos los productos se asignan al origen predeterminado, asociando todas las cantidades a dicho origen. El Source predeterminado se asigna al Stock predeterminado, con el sitio web predeterminado asociado.

## Solución

Si tiene más de un sitio web, debe añadir estos sitios web como Sales Channel a la acción predeterminada u otras acciones personalizadas.

Consulte la sección [Stock de la guía de usuario/wiki](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage) en nuestra guía de usuario para obtener más información sobre cómo hacerlo.
