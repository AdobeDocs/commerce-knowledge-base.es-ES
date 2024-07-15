---
title: "Error de implementación: no se puede aplicar el parche de MDVA-43395"
description: Este artículo proporciona una solución al problema, donde al intentar aplicar el parche MDVA-43395 se produce un error en la implementación.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Error de implementación: no se puede aplicar el parche de MDVA-43395

Este artículo proporciona una solución al problema, donde al intentar aplicar el parche MDVA-43395 se produce un error en la implementación.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Problema

No puede aplicar el parche MDVA-43395.

## Causa

Los comerciantes de la nube no necesitan aplicar el parche MDVA-43395 por separado si tienen instalado [magento/magento-cloud-patch 1.0.16](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016), que ya incluye el parche.

## Solución

Para resolver el problema, quite los parches MDVA-43395 y MDVA-43443 del directorio `m2-hotfixes` y vuelva a implementarlos.

Si pudiera aplicar el parche MDVA-43443 a través del directorio `m2-hotfixes`, aún tendría que eliminarlo como se mencionó anteriormente. Las versiones futuras de Adobe Commerce tendrán estos parches ya contenidos, por lo que podría provocar errores en la implementación si se actualizara más tarde.

Para comprobar si se ha aplicado la revisión, ejecute el comando `vendor/bin/magento-patches -n status |grep 43443`.
Si muestra varios resultados como este, debe quitar el parche MDVA-43443 de la carpeta `m2-hotfixes`:

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Lectura relacionada

* [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.
* [Parches de nube para Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) en nuestra documentación para desarrolladores.
