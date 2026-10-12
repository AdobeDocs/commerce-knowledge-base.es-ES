---
title: La aplicación de un parche desactiva el sitio
description: Este artículo trata sobre el problema en el que un parche que acaba de aplicar elimina el sitio. Para resolverlo, puede quitar el parche.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '289'
ht-degree: 0%
---
# La aplicación de un parche desactiva el sitio

Este artículo trata sobre el problema en el que un parche que acaba de aplicar elimina el sitio. Para resolverlo, puede quitar el parche.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación), todas las versiones compatibles
* Magento Open Source, todas las versiones

## Problema

Después de aplicar un parche, el sitio se bloquea.

## Causa

Este problema podría deberse a una incompatibilidad de versión entre el parche que acaba de aplicar al sitio web, las personalizaciones, otros parches que ha aplicado en el pasado o algún otro error.

## Solución

Retire el parche. El método de eliminación de parches es diferente para Adobe Commerce en la infraestructura en la nube que para Adobe Commerce local y Magento Open Source.

### Magento Open Source, todas las versiones 1.X

Para las versiones de Magento Open Source 1.X,

* Ejecute el siguiente comando SSH: `h SUPEE_patch --revert `

### Adobe Commerce local, Magento Open Source, todas las versiones de la versión 2.x

Para las versiones locales de Adobe Commerce y Magento Open Source 2.x,

1. Ejecute el siguiente comando SSH:

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (Si el comando anterior no funciona, intente usar `-p2` en lugar de `-p1`)

1. Para que se reflejen los cambios, actualice la caché en el Administrador en **Sistema** > **Administración de caché**.

### Adobe Commerce en la infraestructura en la nube, todas las versiones

Para Adobe Commerce en la infraestructura en la nube, todas las versiones,

1. Quitar los `%patch_name%.composer.patch` archivos del directorio `m2-hotfixes`.
1. Confirme e inserte los cambios de código:

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Lectura relacionada

* [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) en nuestra base de conocimiento de soporte.
