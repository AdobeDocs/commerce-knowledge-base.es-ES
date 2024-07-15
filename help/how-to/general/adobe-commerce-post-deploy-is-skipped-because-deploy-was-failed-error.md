---
title: Adobe Commerce * la implementación posterior se ha omitido porque la implementación ha fallado * error
description: "Este artículo explica cómo investigar un error de implementación: *Post-deploy se omite porque la implementación falló*"
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Se ha omitido la implementación posterior de Adobe Commerce *porque se produjo un error en la implementación*

Este artículo explica cómo investigar un error de implementación: *Post-deploy se omite porque la implementación falló*, lo que ocurre durante la implementación en diferentes entornos, por ejemplo, al actualizar.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

La implementación falla y devuelve un mensaje de error genérico, por lo que no está claro cómo resolver el error.

## Causa

Indeterminado: la causa de este mensaje de error depende del código y la base de datos implementados.

## Cómo investigar el error de implementación

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

Para obtener el seguimiento de errores con el fin de determinar la causa real, SSH al servidor y compruebe el archivo de registro `var/log/install_upgrade.log`.
