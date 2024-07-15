---
title: Rendimiento lento debido a páginas no almacenables en caché
description: Este artículo proporciona soluciones para aumentar los tiempos de carga del sitio web o las interrupciones debido a que la caché de toda la página (por ejemplo, Rápidamente) se ha deshabilitado para cualquier bloque en cualquier página que necesite almacenarse en caché.
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Rendimiento lento debido a páginas no almacenables en caché

Este artículo proporciona soluciones para aumentar los tiempos de carga del sitio web o las interrupciones debido a que la caché de toda la página (por ejemplo, Rápidamente) se ha deshabilitado para cualquier bloque en cualquier página que necesite almacenarse en caché.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.x.x
* Adobe Commerce local 2.x.x

### Problema

El sitio experimenta un rendimiento lento porque hay bloques de caché en páginas que deben ser almacenables en caché pero que se han establecido en `cacheable="false"`

### Causa

Hay páginas que Adobe Commerce debe almacenar en caché. Estas páginas tienen el mayor rendimiento. Cada solicitud de estos tipos de páginas, no desde la caché, hace que Adobe Commerce funcione más lentamente.

Estas páginas son:

* Categoría de catálogo (PLP)
* Página de detalles del producto (PDP)
* Páginas de contenido estático (página de inicio, contacto, etc.)

Almacenable en caché e inalmacenable en caché son términos utilizados para indicar si una página debe almacenarse en caché o no. De forma predeterminada, todas las páginas se pueden almacenar en caché. Sin embargo, si algún bloque de un diseño se designa como no almacenable en caché, toda la página no se puede almacenar en caché.

La captura de pantalla siguiente muestra un bloque con una configuración `cacheable="false”` ** ** que crea una página que no se puede almacenar en caché.

![no almacenable en caché_kb.png](assets/non_cacheable_kb.png)

Algunos ejemplos de páginas no almacenables en caché son: comparar productos, carro de compras y páginas de cierre de compra.

La siguiente lista de páginas no se almacena en caché (se evitan las memorias caché de Rápido, Bloque y Diseño). Esto ocurre debido a la configuración &quot;almacenable en caché&quot; del diseño.

### Solución

Compruebe si los archivos especificados arriba tienen la configuración `cacheable="false”` Si es así, compruebe si esta configuración es necesaria o necesaria.

* Si es necesario, considere la posibilidad de mover bloques no almacenables en caché a [mecanismo de contenido privado](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=private%20co) en su lugar.
* Si no es necesario, quite el atributo `cacheable="false”` y vacíe la caché de diseño.

>[!NOTE]
>
>Para Adobe Commerce en la infraestructura en la nube 2.4.1 y versiones posteriores, puede usar la [Herramienta de análisis de todo el sitio](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) para comprobar automáticamente si la caché de toda la página no está configurada correctamente.

### Lectura relacionada

[Descripción general de la caché de Adobe Commerce](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=cacheable%2) en nuestra documentación para desarrolladores.
