---
title: El menú principal (Categorías) no se muestra en las subpáginas que tengan activada la opción Rápidamente
description: Este artículo proporciona una corrección para el caso de que el menú principal (o el [menú Navegación superior de categoría](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) en nuestra guía del usuario) no se muestre en la tienda para subpáginas (por ejemplo, *blog/página*) cuando Fastly o Varnish están habilitados.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# El menú principal (Categorías) no se muestra en las subpáginas que tengan activada la opción Rápidamente

Este artículo proporciona una corrección para cuando el menú principal (o el [Menú de navegación superior de categoría](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) en nuestra guía del usuario) no se muestra en la tienda para subpáginas (por ejemplo, *blog/página*) cuando Fastly o Varnish está habilitado.

**Causa:** los no permitidos `/` carácter (barra) en el *Clave de URL* de la página (Configuración de optimización del motor de búsqueda). El carácter suele añadirse cuando *Ruta de URL* (con ubicación de página completa) se especifica por error en lugar de *Clave de URL*: por ejemplo, *blog/página\_nombre* en lugar de solo *page\_name*.

**Solución:** elimine el `/` carácter (barra diagonal); para *Clave de URL* , especifique solo el nombre de la página.

## Versiones afectadas

* Adobe Commerce local 2.X.X
* Adobe Commerce en infraestructura en la nube 2.X.X
* Fastly o barniz

## Problema

El menú principal (también denominado [Menú de navegación superior de categoría](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) en nuestra guía del usuario) no se muestra en la tienda para subpáginas cuando Fastly u otros servicios basados en Varnish están habilitados.

## Causa

El problema se debe a que no está permitido `/` carácter (barra), agregado a *Clave de URL* (Configuración de optimización del motor de búsqueda).

El carácter suele añadirse cuando *Ruta de URL* (con la ubicación de la página completa, incluido el recurso o directorio principal de la página) se especifica por error en lugar de *Clave de URL*: por ejemplo, *blog/página\_nombre* en lugar de solo *page\_name*.

![Parámetro de clave URL para la configuración de SEO](assets/seo_url_key.png)

## Solución

Retire el `/` carácter (barra diagonal) de *Clave de URL* para todas las páginas de la tienda.

En otras palabras, utilice *Clave de URL* en lugar de *Ruta de URL*: mencione solo el nombre de página sin recurso/directorio principal.

### Recommendations en jerarquía de páginas y SEO

Para establecer la jerarquía de páginas, utilice el **Jerarquía** del menú Editar página.

![Configuración de jerarquía](assets/hierarchy_hr.png)

También puede utilizar el **Contenido** > **Elementos** > **Jerarquía** menú: para obtener soluciones de jerarquía más complejas.

Para fines de SEO en páginas de producto, utilice las reescrituras de URL (**Marketing** > **SEO y búsqueda** > **Reescrituras de URL**).

## Más información en nuestra guía de usuario

El *Clave de URL* parámetro para SEO:

* [Optimización del motor de búsqueda](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Adición de una nueva página](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Jerarquía de páginas:

* [Información general](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Adición de un nodo](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
