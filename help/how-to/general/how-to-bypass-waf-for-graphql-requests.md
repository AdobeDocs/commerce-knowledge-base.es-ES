---
title: Cómo evitar WAF para solicitudes de GraphQL
description: Este artículo explica cómo evitar WAF para solicitudes de GraphQL.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%
---
# Cómo evitar WAF para solicitudes de GraphQL

En este artículo se explica cómo omitir WAF para las solicitudes de GraphQL cuando el WAF [!DNL Fastly] está bloqueando sus solicitudes de GraphQL.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Causa

Debido a la naturaleza inherente de las solicitudes de GraphQL, puede haber muchos caracteres repetidos que pueden almacenar en déclencheur el bloqueo de falsos positivos de las solicitudes por parte de [!DNL Fastly] WAF.

## Solución

1. Omita el WAF para estas solicitudes agregando un fragmento personalizado a través del módulo de Magento [!DNL Fastly]:

   tipo: recv
   prioridad: 15
   contenido:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Haga clic en **[!UICONTROL Upload VCL to Fastly]**.

## Lectura relacionada

* [Firewall de aplicaciones web (WAF)](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) en la guía de Commerce en infraestructura de nube.
* [Introducción a VCL personalizado](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) en la guía de Commerce en infraestructura de nube.
