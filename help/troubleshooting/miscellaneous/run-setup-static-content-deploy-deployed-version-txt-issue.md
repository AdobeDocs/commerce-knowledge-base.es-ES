---
title: run `setup:static-content:problema deploy` deployed_version.txt
description: Este artículo proporciona una corrección para el error "deployed_version.txt" no se puede escribir al ejecutar la configuración:static-content:deploy` comando manualmente.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# correr `setup:static-content:deploy` problema deployed_version.txt

Este artículo proporciona una corrección para `deployed_version.txt` no es un error grabable al ejecutar el `setup:static-content:deploy` comando manualmente.

## Problema

Si sigue las recomendaciones de Adobe Commerce sobre la infraestructura en la nube para utilizar [Administración de configuración](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) (y mueva la generación de recursos estáticos a la fase de compilación para reducir el tiempo de inactividad del sitio web durante la implementación), puede encontrar el siguiente error al ejecutar el `setup:static-content:deploy` comando manualmente:

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

Si aún desea ejecutar la implementación de contenido estático, elimine los enlaces simbólicos en la `pub/static` y ejecute el `setup:static-content:deploy` comando de nuevo:

```
find pub/static/ -maxdepth 1 -type l -delete
```
