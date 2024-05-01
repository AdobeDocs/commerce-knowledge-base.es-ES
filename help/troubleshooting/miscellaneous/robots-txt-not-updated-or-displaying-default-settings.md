---
title: robots.txt no se ha actualizado para mostrar la configuración predeterminada
description: El artículo proporciona una solución para cuando ha configurado `robots.txt` correctamente, por ejemplo, según [Prácticas recomendadas para robots.txt de Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048754931), pero `robots.txt` no se actualiza o muestra la configuración predeterminada.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt no se ha actualizado para mostrar la configuración predeterminada

El artículo proporciona una solución para cuando haya configurado `robots.txt` correctamente, por ejemplo, por [Prácticas recomendadas para Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) pero el `robots.txt` no se está actualizando o muestra la configuración predeterminada.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.3.x, 2.4.x

## Problema

No se puede cambiar el valor predeterminado `robots.txt` configuración.

<u>Pasos a seguir:</u>

1. Acceda al panel de administración.
1. Añadir contenido a **Contenido** > Diseño > **Configuración** > **Editar instrucción personalizada de`robots.txt`** como el texto &quot;hello&quot; y guarde los cambios.
1. Visite la `robots.txt` url.

<u>Resultado esperado:</u>
`robots.txt` tiene el texto guardado.

<u>Resultado real:</u>

`robots.txt` el archivo no cambia.

## Causa

La indexación por motores de búsqueda está desactivada.

## Solución

Habilite la indexación por motores de búsqueda. Consulte [Configurar la indexación por motor de búsqueda](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html#configure-indexing-by-search-engine) en nuestra documentación para desarrolladores.

## Lectura relacionada

* [Añadir robots de mapa del sitio y de motor de búsqueda](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) en nuestra documentación para desarrolladores.
