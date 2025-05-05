---
title: Error de tiempo de espera de puerta de enlace 504 al guardar una categoría con productos de más de 1k
description: Este artículo sugiere una solución para el problema de tiempo de espera que pueda tener al realizar operaciones con categorías grandes (más de 1k de productos).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Error de tiempo de espera de puerta de enlace 504 al guardar una categoría con productos de más de 1k

Este artículo sugiere una solución para el problema de tiempo de espera que pueda tener al realizar operaciones con categorías grandes (más de 1k de productos).

## Productos y versiones afectados:

* Adobe Commerce en infraestructura en la nube 2.3.3
* Adobe Commerce local 2.3.3
* Magento Open Source 2.3.3

## Problema

Requisitos previos: La opción **Tiendas** > **Configuración** > **CATÁLOGO** > **Catálogo** > **Usar ruta de categorías para las direcciones URL de productos** está establecida en *Sí* para la vista de la tienda.

<u>Pasos a seguir</u>

1. En el Administrador de Commerce, vaya a **Catálogo** > **Categorías**.
1. Abra una categoría grande, como más de 1000 productos asignados.
1. Añada un producto a la categoría.
1. Haga clic en **Guardar categoría**.

<u>Resultado esperado:</u>

Categoría guardada correctamente.

<u>Resultado real:</u>

Después de cinco minutos de guardar el proceso, aparecerá la página de error de tiempo de espera de la puerta de enlace 504.

## Causa

El proceso tarda más tiempo que el tiempo de espera configurado del servidor.

## Solución

Al deshabilitar la opción **Generar reescrituras de URL de &quot;categoría/producto&quot;** se eliminarán todas las reescrituras de URL de categoría/producto de la base de datos y se reducirá significativamente el tiempo necesario para las operaciones con categorías grandes.

>[!WARNING]
>
>Si desactiva esta opción, se eliminarán de forma permanente las reescrituras de URL de categorías/productos sin la capacidad de restaurarlas.

Para deshabilitar la opción **Generar reescrituras de URL de &quot;categoría/producto&quot;**:

1. En el Administrador de Commerce, vaya a **Tiendas** > **Configuración** > **CATÁLOGO** > **Catálogo**.
1. En la esquina superior izquierda de la página de configuración, en el campo **Ámbito**, establezca el ámbito de configuración en *Configuración predeterminada*.
1. Establecer **Generar reescrituras de URL de &quot;categoría/producto&quot;** en *No*.
1. Haga clic en **Guardar configuración**.
1. Limpiar la caché ejecutando    ```bash    bin/magento cache:clean    ```    o en el Administrador de Commerce en **Sistema** > **Herramientas** > **Administración de caché**.

Ahora puede agregar productos a categorías o mover categorías con un gran número de productos, y estas operaciones tardarán mucho menos tiempo y no deberían causar tiempo de espera.

## Lectura relacionada

[Redirecciones automáticas de productos](https://experienceleague.adobe.com/es/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic) en nuestra guía del usuario.
