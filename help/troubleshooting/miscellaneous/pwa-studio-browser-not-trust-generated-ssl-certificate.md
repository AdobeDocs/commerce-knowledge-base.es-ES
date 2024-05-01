---
title: "PWA Studio: el explorador no confía en el certificado SSL generado"
description: Este artículo proporciona una solución a una advertencia de certificado SSL no generada y de confianza en el explorador cuando se navega a una instancia local de la tienda de PWA Studio durante el desarrollo.
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# PWA Studio: el explorador no confía en el certificado SSL generado

Este artículo proporciona una solución a una advertencia de certificado SSL no generada y de confianza en el explorador cuando se navega a una instancia local de la tienda de PWA Studio durante el desarrollo.

## Productos y versiones afectados

PWA Studio para Adobe Commerce

## Problema

El explorador no confía en el certificado SSL generado de la tienda del PWA Studio local.

## Causa

Navegación al sitio de desarrollo/ensayo.

## Solución

En el proyecto de tienda, ejecute el comando para agregar un nombre de host personalizado y un certificado SSL a la instancia de desarrollo local:

```sh
yarn buildpack create-custom-origin ./
```

La generación de certificados está a cargo de [devcert](https://github.com/davewasmer/devcert). Depende de OpenSSL, así que asegúrese de tener una versión actual de openssl en su sistema usando el siguiente comando:

`openssl version`

La versión debe ser 1.0 o superior (o LibreSSL 2, en el caso de OSX High Sierra).

Puede instalar versiones superiores de OpenSSL con [Homebrew](https://brew.sh/) en OSX, [Chocolate](https://chocolatey.org/) en Windows o en el administrador de paquetes de su distribución Linux.

Si está ejecutando Linux, asegúrese de que `libnss3-tools` (o el equivalente) está instalado en su sistema. Para obtener más información, consulte esta sección de la [devcert](https://github.com/davewasmer/devcert#skipcertutil) léame.

Algunos usuarios han sugerido eliminar la carpeta devcert para almacenar en déclencheur la regeneración de certificados.

* Para usuarios de MacOS, esta carpeta se encuentra generalmente en: `{{~/Library/Application Support/devcert }}`
* Para usuarios de Windows, esta carpeta se encuentra generalmente en: `${User}\AppData\Local\devcert`

## Lectura relacionada en nuestra base de conocimiento de soporte

* [PWA Studio: error de confianza de certificado firmado automáticamente](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack se bloquea antes de comenzar la compilación](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: El explorador muestra el error &quot;No se puede proxy a&quot;.](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: Errores de validación al ejecutar el modo de desarrollador](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
