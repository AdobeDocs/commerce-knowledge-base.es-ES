---
title: Error de tiempo de espera de puerta de enlace 504 al guardar una categoría con productos de más de 1k
description: Este artículo sugiere una solución para el problema de tiempo de espera que pueda tener al realizar operaciones con categorías grandes (más de 1k de productos).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

Requisitos previos: **Tiendas** > **Configuración** > **CATÁLOGO** > **Catálogo** > **Utilizar ruta de categorías para URL de productos** se establece en *Sí* para la vista de la tienda.

<u>Pasos a seguir</u>

1. En Commerce Admin, vaya a **Catálogo** > **Categorías**.
1. Abra una categoría grande, como más de 1000 productos asignados.
1. Añada un producto a la categoría.
1. Clic **Guardar categoría**.

<u>Resultado esperado:</u>

Categoría guardada correctamente.

<u>Resultado real:</u>

Después de cinco minutos de guardar el proceso, aparecerá la página de error de tiempo de espera de la puerta de enlace 504.

## Causa

El proceso tarda más tiempo que el tiempo de espera configurado del servidor.

## Solución

Desactivación de la **Generar reescrituras de URL de &quot;categoría/producto&quot;** Esta opción eliminará todas las reescrituras de URL de categorías/productos de la base de datos y reducirá significativamente el tiempo necesario para las operaciones con categorías grandes.

>[!WARNING]
>
>Si desactiva esta opción, se eliminarán de forma permanente las reescrituras de URL de categorías/productos sin la capacidad de restaurarlas.

Para deshabilitar la variable **Generar reescrituras de URL de &quot;categoría/producto&quot;** opción:

1. En el Administrador de Commerce, vaya a **Tiendas** > **Configuración** > **CATÁLOGO** > **Catálogo**.
1. En la esquina superior izquierda de la página de configuración, en **Ámbito** , establezca el ámbito de configuración en *Configuración predeterminada*.
1. Establecer **Generar reescrituras de URL de &quot;categoría/producto&quot;** hasta *No*.
1. Clic **Guardar configuración**.
1. Limpiar la caché ejecutando    ```bash    bin/magento cache:clean    ```    o en el Administrador de Commerce, en **Sistema** > **Herramientas** > **Administración de caché**.

Ahora puede agregar productos a categorías o mover categorías con un gran número de productos, y estas operaciones tardarán mucho menos tiempo y no deberían causar tiempo de espera.

## Lectura relacionada

[Redirecciones automáticas de productos](https://docs.magento.com/user-guide/v2.3/marketing/url-redirect-product-automatic.html) en nuestra guía del usuario.
