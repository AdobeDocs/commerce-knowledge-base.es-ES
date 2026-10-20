---
title: 'ERROR: error de calentamiento en Adobe Commerce en la infraestructura en la nube'
description: 'Este artículo proporciona una solución para cuando la caché de la página se calienta y falla con un error:'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a5bb7b49f18f098b8706ba8b3187a7ae81059940
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%
---
# ERROR: error de calentamiento en Adobe Commerce en la infraestructura en la nube

Este artículo proporciona una solución para cuando la caché de la página se calienta y falla con un error:

*ERROR: error en la preparación:`<website link>`*

## Productos y versiones afectados

* Adobe Commerce en la infraestructura de la nube, todas [las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Error de calentamiento de la caché.

<u>Pasos a seguir</u>:

Iniciar operaciones de calentamiento de caché.

<u>Resultado esperado</u>:

Páginas o cargas de sitios completos.

<u>Resultado real</u>:

El sitio no está disponible o el tiempo de respuesta es demasiado alto. *ERROR: error en la preparación:`<website link>`*

## Causa

El calentamiento de la caché no funciona con el control de acceso HTTP habilitado.

## Solución

Asegúrese de que no tiene habilitado el control de acceso: vaya a la rama o entorno específico, haga clic en el icono **Configuración** y compruebe la configuración de **control de acceso HTTP**; en este caso, no se puede calentar la caché y hay que deshabilitar el control de acceso.

## Lectura relacionada

* [Guía del usuario de Adobe Commerce > Caché de página completa](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/tools/cache-management#full-page-caching) en nuestra guía del usuario.