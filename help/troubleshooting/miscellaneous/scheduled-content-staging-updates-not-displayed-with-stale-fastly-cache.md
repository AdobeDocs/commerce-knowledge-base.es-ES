---
title: Las actualizaciones programadas de ensayo de contenido no se muestran con la caché de Fastly obsoleta
description: Este artículo proporciona una corrección para los casos en los que las tiendas Adobe Commerce no muestran actualizaciones programadas al utilizar Ensayo de contenido y Rápido. El problema se debe a que la opción de depuración rápida y suave está habilitada de forma predeterminada. Esta función reduce la carga de recursos de la aplicación y solo regenera una nueva caché en una segunda solicitud. Para resolverlo, puede habilitar la página Purgar CMS mediante el administrador de Commerce para que siempre vuelva a generar y ofrezca contenido nuevo.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%
---
# Las actualizaciones programadas de ensayo de contenido no se muestran con la caché de Fastly obsoleta

Este artículo proporciona una corrección para los casos en los que las tiendas Adobe Commerce no muestran actualizaciones programadas al utilizar Ensayo de contenido y Rápido. El problema se debe a que la opción de depuración rápida y suave está habilitada de forma predeterminada. Esta función reduce la carga de recursos de la aplicación y solo regenera una nueva caché en una segunda solicitud. Para resolverlo, puede habilitar la página Purgar CMS mediante el administrador de Commerce para que siempre vuelva a generar y ofrezca contenido nuevo.

## Problema

Actualizaciones programadas para un recurso de contenido de tienda (página, producto, bloque, etc.) no se muestran en la tienda inmediatamente después de la hora de inicio de la actualización. Esto sucede cuando se han programado actualizaciones utilizando la funcionalidad [Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=es).

## Causa

Debido a la funcionalidad de depuración suave de Fastly (habilitada de forma predeterminada), la tienda de Adobe Commerce sigue recibiendo el contenido en caché antiguo (obsoleto) al enviar **la primera** solicitud del recurso actualizado a Fastly. Requiere una segunda solicitud para volver a generar los datos del sitio.

Como resultado, Fastly puede proporcionar contenido obsoleto hasta la segunda solicitud del contenido actualizado.

**Almacenamiento en caché esperado:** Después de programar una actualización para un recurso de contenido mediante Ensayo de contenido, Adobe Commerce envía una solicitud para actualizar la caché a Fastly. Invalida rápidamente el contenido almacenado en caché anterior (sin eliminar el contenido) y comienza a servir el contenido actualizado.

**Almacenamiento en caché real:** Si Fastly sigue ofreciendo el contenido obsoleto al recibir **la primera** solicitud del contenido actualizado, solo enviará contenido correcto y regenerado después de recibir **la segunda** solicitud. Este comportamiento se ha implementado para reducir la carga del servidor mediante la renovación de la caché solo en áreas con tráfico demostrado, sin regenerar la caché para todo el sitio web. Actualiza rápidamente la caché gradualmente, lo que ahorra los recursos de la aplicación.

## Solución

Si la entrega de contenido obsoleto incluso para la primera solicitud es inaceptable, puede desactivar la depuración suave y activar la página Purgar CMS:

1. Inicie sesión en el administrador local de Commerce como administrador.
1. Vaya a **Tiendas** > **Configuración** > **Avanzadas** > **Sistema** > **Caché de página completa**.
1. Expanda **Configuración rápida** y, a continuación, expanda **Avanzada**.
1. Establezca **Usar purga suave** en *No*.
1. Definir **Purgar página de CMS** en *Sí*.
1. Haga clic en **Guardar configuración** en la parte superior de la página.


![purge_options.png](assets/purge_options.png)

## Documentación relacionada

* [Configure las opciones de depuración](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=es) en la Guía de infraestructura de Commerce en la nube.
* [Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=es) en la documentación de contenido y diseño.
* [Proporcionar contenido obsoleto](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) en la documentación de Fastly.
