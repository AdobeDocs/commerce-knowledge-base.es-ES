---
title: El comando de instalación del Compositor anula el archivo .gitignore, Adobe Commerce
description: Este artículo proporciona una solución para cuando el compositor anula un archivo ".gitignore" rastreado en Adobe Commerce en las infraestructuras en la nube 2.4.2-p1 y 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# El comando de instalación del Compositor anula el archivo .gitignore, Adobe Commerce

Este artículo proporciona una solución para cuando se realiza un seguimiento de `.gitignore` composer anula el archivo en Adobe Commerce en cloud Infrastructure 2.4.2-p1 y 2.3.7.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube 2.4.2-p1 y 2.3.7.

## Problema

`.gitignore` se está sobrescribiendo el archivo al ejecutar el comando de instalación del compositor.

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
   1. `git commit -m "Init"` # archivo enviado al repositorio
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

`.gitignore` no se sobrescribe con composer.

<u>Resultado real</u>:

`.gitignore` es anulado por cada ejecución de instalación del compositor.

## Solución

Para mantener la personalización `.gitignore file` debe ignorarlo en la sección `magento-deploy-ignore` sección.

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

* [¡El archivo .gitignore rastreado es anulado por el compositor!](https://github.com/magento/magento2/issues/32888) en GitHub de Magento2.
