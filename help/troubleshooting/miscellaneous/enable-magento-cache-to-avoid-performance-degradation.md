---
title: Habilitar caché para evitar la degradación del rendimiento
description: Este artículo explica cómo resolver un problema de sitio lento causado por la deshabilitación de ciertos tipos de caché de Adobe Commerce.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
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
source-wordcount: '366'
ht-degree: 0%
---
# Habilitar caché para evitar la degradación del rendimiento

Este artículo explica cómo resolver un problema de sitio lento causado por la deshabilitación de ciertos tipos de caché de Adobe Commerce.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* Adobe Commerce local 2.2.x, 2.3.x

## Problema

Observará una degradación del rendimiento. Por ejemplo, la página Cierre de compra se carga lentamente o el valor Apdex disminuye en New Relic.

## Causa

Una razón para la degradación del rendimiento puede ser que se deshabiliten ciertos tipos de caché de Adobe Commerce.

## Solución

1. En primer lugar, compruebe el estado de la caché de Adobe Commerce para ver si este es el problema. Para ello, [SSH a su entorno](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) y ejecute el siguiente comando:

   ```bash
   php bin/magento cache:status
   ```

   Esto mostraría el estado de cada tipo de caché (&quot;0&quot; para deshabilitado, &quot;1&quot; para habilitado). O puede obtener esta información en el archivo `app/etc/env.php`.

1. Investigue los tipos de caché deshabilitados. Todos los tipos de caché de Adobe Commerce deben habilitarse, a menos que reciba directrices alternativas de Adobe. Las extensiones de terceros no deben requerir la desactivación de la caché de Adobe Commerce.
1. Si la investigación confirma que algunos tipos de caché están deshabilitados por error, actívelos ejecutando el siguiente comando para cada tipo de caché: `php bin/magento cache:enable <your_disabled_cache_type>`

Si tiene dudas o preguntas sobre si cierto tipo de caché de Adobe Commerce se puede o se debe deshabilitar, [póngase en contacto con el servicio de atención al cliente de Adobe Commerce](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) para obtener recomendaciones.

## Lectura relacionada

Documentación de la caché de Adobe Commerce en nuestra documentación para desarrolladores:

* [Resumen de caché de Adobe Commerce](https://developer.adobe.com/commerce/frontend-core/guide/caching)
* [Administrar la caché](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/cli/manage-cache)

Otros posibles motivos de los problemas de rendimiento y sus soluciones:

* [Deshabilitar la salida del titular de Adobe Commerce para mejorar el rendimiento del sitio](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-26909)
* [Las tablas MySQL son demasiado grandes](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [Lento rendimiento, crons lentos y de larga duración](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-42802)
