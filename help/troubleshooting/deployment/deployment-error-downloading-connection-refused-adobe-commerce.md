---
title: 'Error de implementación: *error 7 al descargar... puerto 443: Conexión rechazada*'
description: 'Este artículo proporciona una solución para el error de implementación: *"error 7 al descargar ... puerto 443: conexión rechazada"*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
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
source-wordcount: '286'
ht-degree: 0%
---
# Error de implementación: *error 7 al descargar... puerto 443: conexión rechazada*

Este artículo proporciona una solución para el problema cuando la implementación falla con el siguiente mensaje de error:

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Versiones afectadas

Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

La implementación falla con un mensaje de **curl error 7**.

<u>Pasos a seguir</u>:

Déclencheur de una implementación.

<u>Comportamiento esperado</u>:

La implementación es correcta.

<u>Comportamiento real</u>:

La implementación falla y aparece el siguiente error: *curl error 7 al descargar ... puerto 443: Conexión rechazada* en el registro de implementación.

## Causa

Esto puede deberse a que se ha perdido la conexión de caché con el repositorio.

## Solución

Pida a un superusuario del proyecto que ejecute este comando:

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Para comprobar quién es un superusuario en el proyecto, consulte [Ver la función de proyecto de un usuario](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=es#view-a-user’s-project-role) en la Guía de infraestructura de Commerce en la nube.

## Lectura recomendada

* [Solucionador de problemas de implementación de Adobe Commerce](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-29640).
* No se pudo acceder a [Adobe Commerce en el repositorio en la nube: error 403 prohibido o 404 no encontrado al implementar](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html?lang=es).
* [La implementación falla con &quot;Error al generar el proyecto: Error en el vínculo de compilación con el código de estado 1&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html?lang=es).
