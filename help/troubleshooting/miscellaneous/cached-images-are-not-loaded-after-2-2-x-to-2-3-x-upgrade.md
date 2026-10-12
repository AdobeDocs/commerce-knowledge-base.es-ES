---
title: Las imágenes en caché no se cargan después de la actualización de 2.2.X a 2.3.X
description: Este artículo proporciona la solución al problema de que las imágenes en caché no se muestren después de actualizar de Adobe Commerce en la infraestructura en la nube 2.2.X a 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
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
source-wordcount: '287'
ht-degree: 0%
---
# Las imágenes en caché no se cargan después de la actualización de 2.2.X a 2.3.X

Este artículo proporciona la solución al problema de que las imágenes en caché no se muestren después de actualizar de Adobe Commerce en la infraestructura en la nube 2.2.X a 2.3.X.

## Versiones y ediciones afectadas:

* Arquitectura de plan Pro de Adobe Commerce en la infraestructura en la nube 2.2.X, 2.3.X

## Problema

Después de actualizar Adobe Commerce de 2.2.X a 2.3.X, las imágenes de producto en caché no están disponibles y se muestra una página 404 en su lugar.

El problema se debe al conjunto de configuración de Nginx incorrecto en `.magento.app.yaml`: `index.php` (o ninguno) se usa para la ubicación `"/media"` en lugar de `passthru: /get.php`.

## Solución

1. Compruebe su archivo de configuración de `.magento.app.yaml`, en la ubicación `"/media"`. La configuración correcta tiene el siguiente aspecto:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Si `passthru` no está establecido en `"/get.php"` y `expires` no está establecido, siga estos pasos.
1. Corrija el archivo de configuración.
   * Plan de inicio: corrija el archivo usted mismo e inserte los cambios.
   * Plan Pro:
   * Integración: corrija el archivo usted mismo e inserte los cambios.
   * Ensayo y producción: corrija el archivo usted mismo, inserte los cambios y cree un [vale de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) para que se aplique.

1. Habilite la optimización de imágenes rápida en el administrador de Commerce (la configuración de Fastly debe ser anterior), tal como se describe en <https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization>.

Si la configuración es correcta, pero el problema persiste, continúa investigando o ponte en contacto con el [Soporte técnico de Adobe Commerce](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).
