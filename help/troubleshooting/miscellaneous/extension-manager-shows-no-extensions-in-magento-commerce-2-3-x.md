---
title: El Extension Manager no muestra extensiones en Adobe Commerce 2.3.x
description: Este artículo proporciona una solución para las extensiones que faltan en el Extension Manager de administración en Adobe Commerce 2.3.x después de comprar extensiones a través del Commerce Marketplace.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# El Extension Manager no muestra extensiones en Adobe Commerce 2.3.x

Este artículo proporciona una solución para las extensiones que faltan en el Extension Manager de administración en Adobe Commerce 2.3.x después de comprar extensiones a través del Commerce Marketplace.

## Productos y versiones afectados

* Adobe Commerce versión (todos los métodos de implementación) 2.3.x

## Problema

Cuando compra extensiones a través del Commerce Marketplace, no puede instalarlas con el Extension Manager principal de Adobe Commerce. Al añadir las claves de acceso y sincronizar con Marketplace, el Extension Manager no muestra extensiones.

La **solución** para el problema es usar la instalación de Adobe Commerce desde la línea de comandos como se muestra en [Instalación general de CLI](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/extensions) en nuestra documentación para desarrolladores.

<u>Pasos a seguir</u>:

1. Adquiera una extensión a través del Commerce Marketplace.
1. Añada las claves de acceso de la extensión y sincronícelas con Marketplace.
1. Vaya a la sección Extension Manager del Administrador.

<u>Resultado esperado</u>:

La extensión aparece en la sección Extension Manager del Administrador de Commerce.

<u>Resultado real</u>:

**No aparece ninguna extensión en la sección Extension Manager del administrador de Commerce, de forma similar a la imagen siguiente:**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## Solución

Use la instalación de Adobe Commerce desde la línea de comandos como se muestra en [Instalación general de CLI](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/extensions) en nuestra documentación para desarrolladores.
