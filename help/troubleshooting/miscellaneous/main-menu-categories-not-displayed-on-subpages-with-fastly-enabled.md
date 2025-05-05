---
title: El menú principal (Categorías) no se muestra en las subpáginas que tengan activada la opción Rápidamente
description: Este artículo proporciona una corrección para el caso de que el menú principal (o el [menú Navegación superior de categoría](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html?lang=es) en nuestra guía del usuario) no se muestre en la tienda para subpáginas (por ejemplo, *blog/página*) cuando Fastly o Varnish están habilitados.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# El menú principal (Categorías) no se muestra en las subpáginas que tengan activada la opción Rápidamente

Este artículo proporciona una corrección cuando el menú principal (o el [menú de navegación superior por categorías](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) de nuestra guía del usuario) no se muestra en la tienda para subpáginas (por ejemplo, *blog/página*) cuando Fastly o Varnish están habilitados.

**Causa:** el carácter (barra) `/` no permitido en el parámetro *URL Key* de la página (configuración de optimización del motor de búsqueda). El carácter generalmente se agrega cuando se especifica por error *Ruta de URL* (con ubicación de página completa) en lugar de *Clave de URL*: por ejemplo, *blog/página\_name* en lugar de solo *página\_name*.

**Solución:** quita el carácter `/` (barra diagonal); para el parámetro *URL Key*, especifica solamente el nombre de página.

## Versiones afectadas

* Adobe Commerce local 2.X.X
* Adobe Commerce en infraestructura en la nube 2.X.X
* Fastly o barniz

## Problema

El menú principal (también conocido como [menú de navegación superior por categorías](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) en nuestra guía del usuario) no se muestra en la tienda para las subpáginas cuando está habilitado Fastly u otros servicios basados en Varnish.

## Causa

El problema se debe al carácter (barra) `/` no permitido, agregado al parámetro *URL Key* (configuración de optimización del motor de búsqueda).

El carácter generalmente se agrega cuando se especifica por error *Ruta de URL* (con ubicación de página completa, incluido el recurso o directorio principal de la página) en lugar de *Clave de URL*: por ejemplo, *blog/página\_name* en lugar de solo *página\_name*.

![Parámetro de clave de URL para la configuración de SEO](assets/seo_url_key.png)

## Solución

Elimina el carácter `/` (barra diagonal) del parámetro *Clave de URL* para todas las páginas de tu tienda.

En otras palabras, use *clave de URL* en lugar de *ruta de URL*: mencione solo el nombre de página sin recurso o directorio principal.

### Recommendations en jerarquía de páginas y SEO

Para establecer la jerarquía de páginas, utilice la sección **Jerarquía** del menú Editar página.

![Configuración de jerarquía](assets/hierarchy_hr.png)

También puede usar el menú **Contenido** > **Elementos** > **Jerarquía** para obtener soluciones de jerarquía más complejas.

Para fines de SEO en páginas de productos, use las reescrituras de URL (**Marketing** > **SEO y búsqueda** > **reescrituras de URL**).

## Más información en nuestra guía de usuario

El parámetro *URL Key* para SEO:

* [Optimización del motor de búsqueda](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Adición de una nueva página](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Jerarquía de páginas:

* [Información general](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Adición de un nodo](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
