---
title: Deshabilitar la salida del titular de Adobe Commerce para mejorar el rendimiento del sitio
description: Este artículo proporciona una corrección para el bajo rendimiento del sitio. El bajo rendimiento del sitio puede deberse a que el módulo Magento_Banner esté habilitado, pero no se haya utilizado. Deshabilitar la salida del módulo puede mejorar el rendimiento del sitio. Revise el artículo para ver los pasos de resolución.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Deshabilitar la salida del titular de Adobe Commerce para mejorar el rendimiento del sitio

Este artículo proporciona una corrección para el bajo rendimiento del sitio. El bajo rendimiento del sitio puede deberse a `Magento_Banner` módulo activado pero no utilizado. Deshabilitar la salida del módulo puede mejorar el rendimiento del sitio. Revise el artículo para ver los pasos de resolución.

>[!NOTE]
>
>Si utiliza la funcionalidad Banner de Adobe Commerce, consulte la [AJAX Las solicitudes de alto rendimiento de los recursos provocan un rendimiento deficiente](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) artículo en nuestra base de conocimiento de soporte para recomendaciones sobre cómo evitar problemas de rendimiento causados por solicitudes de Ajax excesivas.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube v.2.x.x
* Adobe Commerce local v.2.2.x y 2.3.x

## Problema

El `Magento_Banner` El módulo está habilitado, pero no se utiliza.

Para comprobar si este es el caso:

Para Adobe Commerce en la infraestructura en la nube 2.2.x:

1. Inicie sesión en el administrador de Commerce.
1. Vaya a **Contenido** > *Elementos* > **Titulares**.
1. Si la cuadrícula que se muestra en esta página está vacía, no tiene titulares.

Si no ve el **Titulares** opción en **Contenido** > *Elementos*, este no es el caso y no se pueden aplicar las recomendaciones de este artículo.

Para Adobe Commerce en la infraestructura en la nube 2.3.x (la funcionalidad era [se ha cambiado el nombre en la versión 2.3.x](https://devdocs.magento.com/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Inicie sesión en el administrador de Commerce.
1. Vaya a **Contenido** > *Elementos >*  **Bloques dinámicos**.
1. Si la cuadrícula que se muestra en esta página está vacía, no tiene ningún bloque dinámico (titulares).

Si no ve el **Bloques dinámicos** opción en **Contenido** > *Elementos*, este no es el caso y no se pueden aplicar las recomendaciones de este artículo.

## Causa

Si la variable `Magento_Banner` Cuando el módulo está habilitado, Adobe Commerce envía solicitudes de Ajax desde la tienda al servidor para obtener la información del titular. Estas solicitudes de Ajax tienen un impacto en el rendimiento, especialmente en condiciones de alta carga (gran volumen y alto tráfico). Si no se utiliza la funcionalidad, se recomienda deshabilitar la salida del módulo. No se recomienda deshabilitar el módulo debido a los problemas de dependencia.

## Solución

>[!WARNING]
>
>Recomendamos encarecidamente probar los cambios en [Entorno de ensayo/integración](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) primero, antes de aplicarlo a Producción. También recomendamos realizar una copia de seguridad reciente antes de realizar cualquier manipulación.

1. Desactivar el `Magento_Banner` salida del módulo, tal como se describe en [Deshabilitar salida del módulo](https://devdocs.magento.com/guides/v2.3/config-guide/config/disable-module-output.html) en nuestra documentación para desarrolladores. El nombre de módulo que debe utilizar es `Magento_Banner`.
1. Implemente su código. Para Adobe Commerce en la infraestructura en la nube, implemente como se describe en la [Implementar la tienda](https://devdocs.magento.com/guides/v2.3/cloud/live/stage-prod-live.html) artículo en nuestra documentación para desarrolladores.
