---
title: 'PWA Studio: el explorador no puede resolver el sitio .local.pwadev'
description: Este artículo proporciona una solución para los casos en los que otro programa o proceso ha editado su [archivo host] (https://en.wikipedia.org/wiki/Hosts_(file\) y ha eliminado la entrada del dominio del proyecto.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%
---
# PWA Studio: el explorador no puede resolver el sitio .local.pwadev

Este artículo proporciona una solución para los casos en los que otro programa o proceso haya editado su [archivo host]&#x200B;(https://en.wikipedia.org/wiki/Hosts_(file\) y quitado la entrada del dominio del proyecto.

## Productos y versiones afectados

PWA Studio para Adobe Commerce

## Problema

Al navegar al sitio de desarrollo o ensayo, no puede ver el sitio `.local.pwadev`.

## Causa

PWA Studio permite asignar un nombre de host personalizado y un certificado SSL para el proyecto al equipo local. Esto implica crear una nueva entrada en el archivo host del equipo que se parezca a `my-storefront-project-abc123.local.pwadev`.

Esta entrada indica a cualquier explorador del equipo del desarrollador que mire el proyecto de tienda local cuando acceda a esa dirección URL. Si otro programa o proceso entrara y quitara esa entrada, el explorador no sabría adónde ir y no podría resolver el sitio `.local.pwadev`.

## Solución

Puede [editar manualmente su archivo host](https://docs.rackspace.com/docs/modify-your-hosts-file) para volver a agregar la entrada, pero debe examinar el otro software instalado para ver qué ha sobrescrito el cambio anterior.

## Lectura relacionada en nuestra base de conocimiento de soporte

* [PWA Studio: error de confianza de certificado firmado automáticamente](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack se bloquea antes de comenzar la compilación](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: El explorador muestra el error &quot;No se puede proxy a&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: Errores de validación al ejecutar el modo de desarrollador](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
