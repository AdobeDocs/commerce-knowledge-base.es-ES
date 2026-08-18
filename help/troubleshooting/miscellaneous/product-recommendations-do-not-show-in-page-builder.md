---
title: Las recomendaciones de productos no se muestran en Page Builder
description: Este artículo proporciona una solución para el problema en el que la opción Recomendaciones de productos no se muestra en Page Builder.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Las recomendaciones de productos no se muestran en Page Builder

Este artículo proporciona una solución para el problema en el que la opción Recomendaciones de productos no se muestra en Page Builder.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación)

## Problema

La opción Recomendaciones de productos no se muestra en Page Builder.

## Causa

No hay ninguna opción en Page Builder para agregar Recomendaciones de productos. Recomendaciones de productos para Page Builder es un módulo opcional que se instala por separado.

## Solución

1. Compruebe si ha instalado el módulo por separado ejecutando el comando: `composer show magento/module-page-builder-product-recommendations`
1. Si devuelve el siguiente mensaje: *No se encontró el paquete magento/module-page-builder-product-recommendations*, tendrá que instalarlo ejecutando el comando: `composer require magento/module-page-builder-product-recommendations`

Al habilitar Recomendaciones de productos en Page Builder, podrá [agregar una unidad de recomendación](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) a cualquier contenido creado en Page Builder.

## Lectura relacionada

* [Agregar contenido: recomendaciones de productos](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) en nuestra guía del usuario.
* [Instale y configure Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) en nuestra documentación para desarrolladores.
* [Guía del usuario de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/user-guides/home)
