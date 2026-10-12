---
title: ejecutar problema de `setup:static-content:deploy` deployed_version.txt
description: Este artículo proporciona una corrección para el error "deployed_version.txt" no se puede escribir cuando se ejecuta el comando "setup:static-content:deploy" manualmente.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: d05f97c9-0a96-5792-92cf-f66ce7326e3a
    internal-label: SCD
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%
---
# ejecutar `setup:static-content:deploy` problema deployed_version.txt

Este artículo proporciona una corrección para el error no se puede escribir en `deployed_version.txt` al ejecutar el comando `setup:static-content:deploy` manualmente.

## Problema

Si sigue las recomendaciones de Adobe Commerce sobre la infraestructura en la nube para utilizar la administración de la configuración (y mueve la generación de recursos estáticos a la fase de compilación para reducir el tiempo de inactividad del sitio web durante la implementación), puede encontrar el siguiente error al ejecutar el comando `setup:static-content:deploy` manualmente:

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## Causa

Hemos optimizado el proceso de implementación para reducir el tiempo de inactividad y hemos creado enlaces simbólicos a archivos de recursos estáticos en lugar de copiarlos. La ubicación donde se almacenan los recursos estáticos es de solo lectura, por lo que aparece el mensaje de error anterior.

No se recomienda ejecutar la implementación de contenido estático manualmente porque todos los recursos ya se han generado y no habrá diferencia entre los archivos si lo hace manualmente (los archivos de tema también son de solo lectura, no puede cambiarlos), por lo que no tiene sentido realizar esta operación.

## Solución

Si aún desea ejecutar la implementación de contenido estático, quite los enlaces simbólicos del directorio `pub/static` y ejecute de nuevo el comando `setup:static-content:deploy`:

```
find pub/static/ -maxdepth 1 -type l -delete
```
