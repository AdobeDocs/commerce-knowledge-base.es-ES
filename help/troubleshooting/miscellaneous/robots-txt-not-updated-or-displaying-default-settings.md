---
title: robots.txt no se ha actualizado para mostrar la configuración predeterminada
description: El artículo proporciona una solución para cuando ha configurado &grave;robots.txt&grave; correctamente, por ejemplo, según [Prácticas recomendadas para robots.txt de Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048754931), pero &grave;robots.txt&grave; no se actualiza o muestra la configuración predeterminada.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt no se ha actualizado para mostrar la configuración predeterminada

El artículo proporciona una solución para cuando haya configurado `robots.txt` correctamente, por ejemplo, según las [prácticas recomendadas para Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), pero `robots.txt` no se está actualizando o muestra la configuración predeterminada.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.3.x, 2.4.x

## Problema

No se puede cambiar la configuración predeterminada de `robots.txt`.

<u>Pasos a seguir:</u>

1. Acceda al panel de administración.
1. Agregue contenido a **Contenido** > Diseño > **Configuración** > **Edite la instrucción personalizada de`robots.txt`** archivo, como el texto &quot;hello&quot;, y guarde los cambios.
1. Visite la URL `robots.txt`.

<u>Resultado esperado:</u>
`robots.txt` tiene el texto guardado.

<u>Resultado real:</u>

`robots.txt` archivo no cambia.

## Causa

La indexación por motores de búsqueda está desactivada.

## Solución

Habilite la indexación por motores de búsqueda. Consulte [Configurar la indexación mediante el motor de búsqueda](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine) en nuestra documentación para desarrolladores.

## Lectura relacionada

* [Agregue robots de mapa del sitio y de motor de búsqueda](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) en nuestra documentación para desarrolladores.
