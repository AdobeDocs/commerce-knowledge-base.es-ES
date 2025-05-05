---
title: Sitio no accesible debido al encubrimiento del origen
description: Este artículo proporciona una solución para los casos en los que el administrador o la tienda del sitio de producción o el ensayo de la infraestructura en la nube de Adobe Commerce no sean accesibles.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: b58e182c64b3fad508145d9078619ddbe0e2b887
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Sitio no accesible debido al encubrimiento del origen

Este artículo proporciona una solución para los casos en los que el administrador o la tienda del sitio de producción o el ensayo de la infraestructura en la nube de Adobe Commerce no sean accesibles.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.3.x, 2.4.x

## Problema

https:&#x200B;//mydomain.com.c.&lt;projectid>.magento.cloud/ ya no es accesible.

<u>Pasos a seguir:</u>

1. Inicie sesión en el proyecto.
1. Haga clic en **Acceder al proyecto** para obtener una lista de direcciones URL y SSH.

<u>Resultados reales:</u>

La página no se puede cargar con el siguiente error:

*NET::ERR\_CERT\_INVALID* *Alerta TLS, certificado incorrecto (554):*

<u>Resultados esperados:</u>

La página se carga correctamente.

## Causa

El encubrimiento de origen se ha habilitado, por lo que ya no se puede acceder directamente al origen.

El encubrimiento de origen es una función de seguridad que permite a Adobe Commerce bloquear cualquier tráfico que no sea de Fastly que vaya a la infraestructura de la nube (origen) para evitar ataques DDoS.

## Solución

* Si el sitio de la nube está activo, cambie a https://mydomain.com/.
* Si tiene un sitio activo (que no está en la nube), usando el dominio https://mydomain.com/, configure un subdominio `mcprod.mydomain.com` y actualice la **URL base** a *https://mcprod.mydomain.com* en su lugar, entonces [señale el DNS a Fastly](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#update-dns-configuration-with-development-settings).

## Lectura relacionada

* [Preguntas frecuentes sobre la habilitación del encubrimiento de origen rápido](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) en nuestra base de conocimiento de soporte
* [Lista de comprobación para configurar un nuevo dominio](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain) en nuestra base de conocimiento de soporte
