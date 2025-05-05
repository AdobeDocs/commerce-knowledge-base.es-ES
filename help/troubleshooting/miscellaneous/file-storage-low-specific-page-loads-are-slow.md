---
title: Almacenamiento de archivos bajo, cargas de página específicas lentas
description: Este artículo proporciona una solución para el problema del espacio en disco bajo causado por imágenes grandes y enriquecidas.
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Almacenamiento de archivos bajo, cargas de página específicas lentas

Este artículo proporciona una solución para el problema del espacio en disco bajo causado por imágenes grandes y enriquecidas.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones compatibles
* Adobe Commerce local, todas las versiones compatibles
* Magento Open Source, todas las versiones compatibles

## Problema

El almacenamiento en disco bajo y las cargas de página lentas pueden deberse a imágenes grandes y enriquecidas que usan grandes cantidades de almacenamiento en `pub/media/catalog/products` y al uso compartido del espacio en disco entre ensayo y producción (a menos que se aprovisione un entorno de ensayo dedicado).

## Causa

Las imágenes no están optimizadas para equilibrar el rendimiento con la calidad de visualización.

## Solución

Antes de cargar las imágenes, optimícelas y comprímalas para equilibrar el rendimiento con la calidad de visualización. Esto ayuda a aumentar el espacio y reducir los tiempos de carga de la página. Los archivos PNG ofrecen tamaños más pequeños para las imágenes con grandes áreas de color sólido. Los JPEG dan tamaños más pequeños para todo lo demás. Utilice la compresión más alta (sin una degradación apreciable). Esto suele ser del 60-80%.

Use [Optimización rápida de imágenes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=es) para producir imágenes con un almacenamiento más eficiente.

## Lectura relacionada

Para obtener más información sobre cómo administrar el espacio en disco (si está en Adobe Commerce en una infraestructura en la nube), consulte [Administrar espacio en disco en Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=es) en la Guía de Commerce en infraestructura en la nube.
