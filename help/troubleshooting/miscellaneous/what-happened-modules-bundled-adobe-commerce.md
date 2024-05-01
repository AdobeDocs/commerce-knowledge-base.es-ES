---
title: Módulos que faltan en Adobe Commerce 2.4.4
description: Este artículo proporciona una solución al problema cuando los módulos incluidos en versiones anteriores de Adobe Commerce no están presentes en la versión 2.4.4.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Módulos que faltan en Adobe Commerce 2.4.4

Este artículo proporciona una solución para los casos en los que los módulos incluidos en versiones anteriores de Adobe Commerce no están presentes en 2.4.4.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) todo  [versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

No puede instalar un módulo de terceros o ha detectado que algunas de las extensiones agrupadas principales no están presentes al actualizar a Adobe Commerce 2.4.4. Esto solo debería resultar de instalar un módulo de terceros que requiera una de las extensiones agrupadas eliminadas de Adobe Commerce 2.4.4 o si el proyecto utiliza algunas de las funcionalidades de uno de los módulos eliminados.

* Escenario 1: el proyecto ha utilizado una de las funciones del módulo agrupado principal. El módulo agrupado utilizado no está incluido en Adobe Commerce 2.4.4. Después de actualizar correctamente a Adobe Commerce 2.4.4, se da cuenta de que faltan el módulo y su funcionalidad proporcionada.

* Escenario 2: tiene un módulo instalado en el proyecto actual que depende de uno de los módulos agrupados eliminados.

Este es el comportamiento esperado, ya que las extensiones agrupadas por proveedor se han eliminado de la base de código de Adobe Commerce 2.4.4.

## Solución

Instale/compre las extensiones oficiales por separado. Están disponibles en la [Commerce Marketplace](https://marketplace.magento.com/extensions.html).

## Lectura relacionada

[Extensiones agrupadas por proveedor](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions) en Documentación de Adobe Commerce > Información de la versión > Notas de la versión de Adobe Commerce 2.4.4.
