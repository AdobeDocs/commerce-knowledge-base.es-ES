---
title: El comando de instalación del Compositor anula el archivo .gitignore, Adobe Commerce
description: Este artículo proporciona una solución para cuando el compositor anula un archivo ".gitignore" rastreado en Adobe Commerce en las infraestructuras en la nube 2.4.2-p1 y 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%
---
# El comando de instalación del Compositor anula el archivo .gitignore, Adobe Commerce

Este artículo proporciona una solución para los casos en los que el compositor anula un archivo de seguimiento de `.gitignore` en Adobe Commerce en la infraestructura en la nube 2.4.2-p1 y 2.3.7.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube 2.4.2-p1 y 2.3.7.

## Problema

El archivo `.gitignore` se está sobrescribiendo al ejecutar el comando de instalación del compositor.

<u>Pasos a seguir</u>:


1. Cree un directorio vacío para el espacio de trabajo.
1. Ejecute este comando en el directorio raíz:

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \# o 2.3.7

1. A continuación, ejecute los siguientes comandos:
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. `git commit -m "Init"` archivo # enviado al repositorio
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>Resultado esperado</u>:

El compositor no reemplaza a `.gitignore`.

<u>Resultado real</u>:

`.gitignore` se reemplaza con cada ejecución de instalación del compositor.

## Solución

Para conservar su `.gitignore file` personalizado, debe ignorarlo en la sección `magento-deploy-ignore`.

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## Lectura relacionada

* [El compositor anula el archivo .gitignore que se ha seguido.](https://github.com/magento/magento2/issues/32888) en Magento2 GitHub.
