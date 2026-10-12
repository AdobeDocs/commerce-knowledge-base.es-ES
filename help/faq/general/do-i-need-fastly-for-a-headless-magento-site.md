---
title: ¿Necesito Fastly para un sitio de Adobe Commerce sin encabezado?
description: ¿Necesito Fastly para un sitio de Adobe Commerce sin encabezado?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%
---
# ¿Necesito Fastly para un sitio de Adobe Commerce sin encabezado?

>[!NOTE]
>
>Todos los clientes deben utilizar Fastly para sus entornos de producción y ensayo. Fastly es una red de entrega de contenido (CDN) que proporciona almacenamiento en caché de página completa, optimización de imágenes y servicios de seguridad (DDoS y WAF) como parte de su Adobe Commerce en proyectos de infraestructura en la nube. Estos son componentes principales de la solución de Adobe Commerce, que proporcionan un rendimiento y una seguridad mayores. Estas funciones forman parte de la conformidad con PCI de Adobe. Debe configurar estos servicios de Fastly en los entornos Starter Master, Staging, Pro Staging y Production. Si utiliza Adobe Commerce en una implementación sin encabezado, todo el tráfico de API de Internet público debe pasar por Fastly y le recomendamos encarecidamente que utilice Fastly para almacenar en caché las respuestas de GraphQL. Consulte [Guía para desarrolladores de GraphQL > Almacenamiento en caché con Fastly](https://developer.adobe.com/commerce/webapi/graphql/usage/caching/#caching-with-fastly) en nuestra documentación para desarrolladores.

## **Pregunta**

Estoy desarrollando una implementación sin encabezado de Adobe Commerce. ¿Todavía necesito utilizar Fastly como servicio CDN para ello?

## **Respuesta**

No, tú no. En esta situación, puede omitir el uso de Fastly - al menos, en el comienzo del desarrollo.

La única situación que es posible que no desee habilitar es para una implementación sin encabezado.
Consulte [Nube para Adobe Commerce > Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) en nuestra documentación para desarrolladores.

Aún así, lo más probable es que necesite Fastly para utilizar su certificado SSL.

Todos los clientes de Adobe Commerce en la infraestructura en la nube obtienen un certificado SSL compartido de Fastly como parte del plan de suscripción en la nube. Añadir su propio certificado SSL a Fastly es una opción paga separada y bastante cara. Por lo tanto, recomendamos encarecidamente habilitar Fastly y, al menos, probarlo en los entornos de ensayo y producción antes de lanzarlo, incluso para su sitio web sin encabezado de Adobe Commerce.

## Más información

* [Sitios web sin encabezado: ¿Cuál es el problema con la arquitectura disociada?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) por [Josh Koenig](https://pantheon.io/team/josh-koenig).
* [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) en nuestra documentación para desarrolladores.
