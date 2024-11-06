---
title: Deshabilitar la salida del titular de Adobe Commerce para mejorar el rendimiento del sitio
description: Este artículo proporciona una corrección para el bajo rendimiento del sitio. El bajo rendimiento del sitio puede deberse a que el módulo Magento_Banner esté habilitado, pero no se haya utilizado. Deshabilitar la salida del módulo puede mejorar el rendimiento del sitio. Revise el artículo para ver los pasos de resolución.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Deshabilitar la salida del titular de Adobe Commerce para mejorar el rendimiento del sitio

Este artículo proporciona una corrección para el bajo rendimiento del sitio. El bajo rendimiento del sitio puede deberse a que el módulo `Magento_Banner` se ha habilitado pero no se ha utilizado. Deshabilitar la salida del módulo puede mejorar el rendimiento del sitio. Revise el artículo para ver los pasos de resolución.

>[!NOTE]
>
>Si usa la funcionalidad Banner de Adobe Commerce AJAX, consulte el artículo [Las solicitudes de alto rendimiento de los informes causan un rendimiento deficiente](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) en nuestra base de conocimiento de soporte técnico para obtener recomendaciones sobre cómo evitar problemas de rendimiento causados por solicitudes de Ajax excesivas.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube v.2.x.x
* Adobe Commerce local v.2.2.x y 2.3.x

## Problema

El módulo `Magento_Banner` está habilitado, pero no se usa.

Para comprobar si este es el caso:

Para Adobe Commerce en la infraestructura en la nube 2.2.x:

1. Inicie sesión en el administrador de Commerce.
1. Vaya a **Contenido** > *Elementos* > **Banners**.
1. Si la cuadrícula que se muestra en esta página está vacía, no tiene titulares.

Si no ve la opción **Banners** en **Contenido** > *Elementos*, este no es el caso y no se pueden aplicar las recomendaciones de este artículo.

Para Adobe Commerce en la infraestructura en la nube 2.3.x (la funcionalidad fue [renombrada en la versión 2.3.x](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Inicie sesión en el administrador de Commerce.
1. Vaya a **Contenido** > *Elementos >* **Bloques dinámicos**.
1. Si la cuadrícula que se muestra en esta página está vacía, no tiene ningún bloque dinámico (titulares).

Si no ve la opción **Bloques dinámicos** en **Contenido** > *Elementos*, este no es el caso y no se pueden aplicar las recomendaciones de este artículo.

## Causa

Cuando el módulo `Magento_Banner` está habilitado, Adobe Commerce envía solicitudes de Ajax desde la tienda al servidor para obtener la información del titular. Estas solicitudes de Ajax tienen un impacto en el rendimiento, especialmente en condiciones de alta carga (gran volumen y alto tráfico). Si no se utiliza la funcionalidad, se recomienda deshabilitar la salida del módulo. No se recomienda deshabilitar el módulo debido a los problemas de dependencia.

## Solución

>[!WARNING]
>
>Recomendamos encarecidamente probar primero los cambios en el [entorno de ensayo/integración](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) antes de aplicarlo a Producción. También recomendamos realizar una copia de seguridad reciente antes de realizar cualquier manipulación.

1. Deshabilite la salida del módulo `Magento_Banner`, tal como se describe en [Deshabilitar la salida del módulo](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output) en nuestra documentación para desarrolladores. El nombre de módulo que necesita usar es `Magento_Banner`.
1. Implemente su código. Para Adobe Commerce en la infraestructura en la nube, realice la implementación tal como se describe en el artículo [Implementar su tienda](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) en nuestra documentación para desarrolladores.
