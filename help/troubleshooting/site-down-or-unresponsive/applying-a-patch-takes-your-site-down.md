---
title: La aplicación de un parche desactiva el sitio
description: Este artículo trata sobre el problema en el que un parche que acaba de aplicar elimina el sitio. Para resolverlo, puede quitar el parche.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
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

### Adobe Commerce local, Magento Open Source, todas las versiones de 2.x

Para las versiones locales de Adobe Commerce y Magento Open Source 2.x,

1. Ejecute el siguiente comando SSH:

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (Si el comando anterior no funciona, intente utilizar `-p2` en lugar de `-p1`)

1. Para que se reflejen los cambios, actualice la caché en el Administrador en **Sistema** > **Administración de caché**.

### Adobe Commerce en la infraestructura en la nube, todas las versiones

Para Adobe Commerce en la infraestructura en la nube, todas las versiones,

1. Retire el `%patch_name%.composer.patch` archivo(s) de `m2-hotfixes` directorio.
1. Confirme e inserte los cambios de código:

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Lectura relacionada

* [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.
