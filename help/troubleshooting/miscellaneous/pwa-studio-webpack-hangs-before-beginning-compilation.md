---
title: "PWA Studio: Webpack se bloquea antes de comenzar la compilación"
description: Este artículo habla sobre una solución sugerida para cuando un javascript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) se cuelga durante mucho tiempo antes de comenzar la compilación en Progressive Web App Studio (PWA Studio).
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio: Webpack se bloquea antes de comenzar la compilación

Este artículo trata sobre una solución sugerida para cuando un javascript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) se cuelga durante mucho tiempo antes de comenzar la compilación en Progressive Web App Studio (PWA Studio).

## Productos y versiones afectados

* PWA Studio

## Problema

[Compruebe cuál es la última versión del paquete pwa-buildpack](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack) y el

```yaml
pwa-buildpack
```

el número de versión aparecerá junto al nombre de archivo `package.json`. Si tiene una versión antigua de

```yaml
pwa-buildpack
```

proyecto, el webpack puede colgarse durante mucho tiempo antes de comenzar la compilación.

<u>Pasos a seguir</u>:

<u>Requisitos previos</u>: configura una tienda de PWA Studio, como Venia, con una instancia local de Adobe Commerce y ejecuta una

```yaml
build
```

o

```yaml
watch
```

comando.

<u>Resultado esperado</u>:

* Si se usa la variable    ```yaml    build    ```    , genera los artefactos de compilación para Venia normalmente.
* Si se usa la variable    ```yaml    watch    ```    , inicia la tienda Venia normalmente.

<u>Resultado real</u>:

Su

```yaml
build
```

o

```yaml
watch
```

El comando parecerá bloqueado y no se completará. No se mostrará ningún error.

## Soluciones

Actualice el proyecto con el siguiente comando:

```yaml
yarn upgrade
```

Asegúrese de que tiene una versión actual de openssl en el sistema mediante el siguiente comando:

```yaml
openssl version
```

La versión debe ser 1.0 o superior (o LibreSSL 2, en el caso de OSX High Sierra).

Puede instalar versiones superiores de OpenSSL con [Homebrew](https://brew.sh/) en OSX, [Chocolatey](https://chocolatey.org/) en Windows o el administrador de paquetes de su distribución Linux.

## Lectura relacionada

* [Webpack de JavaScript: Conceptos](https://webpack.js.org/concepts/)
* [Configuración de la tienda Venia](https://magento.github.io/pwa-studio/venia-pwa-concept/setup/)
* [Paquete de PWA](https://magento.github.io/pwa-studio/pwa-buildpack/)
* [Interfaz de línea de comandos buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/reference/buildpack-cli/)
* [Herramientas y bibliotecas: buildpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)
