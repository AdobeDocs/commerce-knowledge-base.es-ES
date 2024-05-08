---
title: Cómo evitar WAF para solicitudes de GraphQL
description: Este artículo explica cómo evitar WAF para solicitudes de GraphQL.
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Cómo evitar WAF para solicitudes de GraphQL

Este artículo explica cómo evitar WAF para solicitudes de GraphQL cuando la variable [!DNL Fastly] WAF está bloqueando sus solicitudes de GraphQL.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Causa

Debido a la naturaleza inherente de las solicitudes de GraphQL, puede haber muchos caracteres repetidos que pueden déclencheur el bloqueo de falsos positivos de las solicitudes por parte de [!DNL Fastly] WAF.

## Solución

1. Omitir el WAF para estas solicitudes agregando un fragmento personalizado a través de [!DNL Fastly] Módulo de Magento:

   tipo: recv prioridad: 15 contenido:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Haga clic en **[!UICONTROL Upload VCL to Fastly]**.

## Lectura relacionada

* [Firewall de aplicaciones web (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) en la guía de Commerce sobre infraestructura en la nube.
* [Introducción a VCL personalizado](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) en la guía de Commerce sobre infraestructura en la nube.

