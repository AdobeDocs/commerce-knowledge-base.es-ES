---
title: Las actualizaciones programadas de ensayo de contenido no se muestran con la caché de Fastly obsoleta
description: Este artículo proporciona una corrección para los casos en los que las tiendas Adobe Commerce no muestran actualizaciones programadas al utilizar Ensayo de contenido y Rápido. El problema se debe a que la opción de depuración rápida y suave está habilitada de forma predeterminada. Esta función reduce la carga de recursos de la aplicación y solo regenera una nueva caché en una segunda solicitud. Para resolverlo, puede habilitar Purgar página de CMS mediante el administrador de Commerce para regenerar y ofrecer siempre contenido nuevo.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Las actualizaciones programadas de ensayo de contenido no se muestran con la caché de Fastly obsoleta

Este artículo proporciona una corrección para los casos en los que las tiendas Adobe Commerce no muestran actualizaciones programadas al utilizar Ensayo de contenido y Rápido. El problema se debe a que la opción de depuración rápida y suave está habilitada de forma predeterminada. Esta función reduce la carga de recursos de la aplicación y solo regenera una nueva caché en una segunda solicitud. Para resolverlo, puede habilitar Purgar página de CMS mediante el administrador de Commerce para regenerar y ofrecer siempre contenido nuevo.

## Problema

Actualizaciones programadas para un recurso de contenido de tienda (página, producto, bloque, etc.) no se muestran en la tienda inmediatamente después de la hora de inicio de la actualización. Esto sucede cuando se han programado actualizaciones utilizando la funcionalidad [Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html).

## Causa

Debido a la funcionalidad de depuración suave de Fastly (habilitada de forma predeterminada), la tienda de Adobe Commerce sigue recibiendo el contenido en caché antiguo (obsoleto) al enviar **la primera** solicitud del recurso actualizado a Fastly. Requiere una segunda solicitud para volver a generar los datos del sitio.

Como resultado, Fastly puede proporcionar contenido obsoleto hasta la segunda solicitud del contenido actualizado.

**Almacenamiento en caché esperado:** Después de programar una actualización para un recurso de contenido mediante Ensayo de contenido, Adobe Commerce envía una solicitud para actualizar la caché a Fastly. Invalida rápidamente el contenido almacenado en caché anterior (sin eliminar el contenido) y comienza a servir el contenido actualizado.

**Almacenamiento en caché real:** Si Fastly sigue ofreciendo el contenido obsoleto al recibir **la primera** solicitud del contenido actualizado, solo enviará contenido correcto y regenerado después de recibir **la segunda** solicitud. Este comportamiento se ha implementado para reducir la carga del servidor mediante la renovación de la caché solo en áreas con tráfico demostrado, sin regenerar la caché para todo el sitio web. Actualiza rápidamente la caché gradualmente, lo que ahorra los recursos de la aplicación.

## Solución

Si la entrega de contenido obsoleto incluso para la primera solicitud es inaceptable, puede desactivar Purga suave y activar la página Purgar CMS:

1. Inicie sesión en el administrador local de Commerce como administrador.
1. Vaya a **Tiendas** > **Configuración** > **Avanzadas** > **Sistema** > **Caché de página completa**.
1. Expanda **Configuración rápida** y, a continuación, expanda **Avanzada**.
1. Establezca **Usar purga suave** en *No*.
1. Definir **Purgar página CMS** en *Sí*.
1. Haga clic en **Guardar configuración** en la parte superior de la página.


![purge_options.png](assets/purge_options.png)

## Documentación relacionada

* [Configure las opciones de depuración](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) en la Guía de infraestructura de Commerce en la nube.
* [Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) en la documentación de contenido y diseño.
* [Proporcionar contenido obsoleto](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) en la documentación de Fastly.
