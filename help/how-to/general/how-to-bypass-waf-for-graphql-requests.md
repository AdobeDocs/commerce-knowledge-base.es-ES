---
title: Cómo evitar WAF para solicitudes de GraphQL
description: Este artículo explica cómo evitar WAF para solicitudes de GraphQL.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Cómo evitar WAF para solicitudes de GraphQL

Este artículo explica cómo omitir WAF para solicitudes de GraphQL cuando el WAF [!DNL Fastly] está bloqueando sus solicitudes de GraphQL.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Causa

Debido a la naturaleza inherente de las solicitudes de GraphQL, puede haber muchos caracteres repetidos que pueden almacenar en déclencheur el bloqueo de falsos positivos de las solicitudes por parte del WAF [!DNL Fastly].

## Solución

1. Omitir el WAF para estas solicitudes agregando un fragmento personalizado a través del módulo de Magento [!DNL Fastly]:

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
