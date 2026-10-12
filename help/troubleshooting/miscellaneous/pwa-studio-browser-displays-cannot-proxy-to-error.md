---
title: 'PWA Studio: El explorador muestra el error "No se puede proxy a"'
description: En este tema se describe una solución cuando el explorador web muestra "*No se puede proxy a*" y la consola muestra un
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%
---
# PWA Studio: El explorador muestra el error &quot;No se puede proxy a&quot;

En este tema se describe una solución cuando el explorador web muestra &quot;*No se puede usar el proxy para*&quot; y la consola muestra un

```
ENOTFOUND
```

error al usar Progressive Web App (PWA) Studio para Adobe Commerce.

## Productos y versiones afectados

* PWA Studio para Adobe Commerce

## Problema

<u>Paso para reproducir</u>:

* Cargue la tienda de Adobe Commerce en un navegador.

<u>Resultado esperado</u>:

* La tienda de Adobe Commerce se carga normalmente en el explorador.

<u>Resultado real</u>:

* Su explorador web muestra el error &quot;*No se puede proxy a*&quot; y la consola muestra un error como:

```
    ENOTFOUND
```


## Causa

NodeJS no puede resolver el nombre de host de su tienda Adobe Commerce.

## Solución

1. Asegúrese de que la tienda de Adobe Commerce se carga en más de un explorador web.
1. Si está ejecutando un servidor DNS local o VPN, agregue una entrada a su archivo host (ubicado en `/etc/hosts`) y asigne manualmente este dominio ([Instrucciones genéricas sobre la edición de archivos host](https://linuxize.com/post/how-to-edit-your-hosts-file/)) para que NodeJS pueda resolverlo.

## Lectura relacionada

* [Documentación de PWA Studio para Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/)
* [Herramientas y bibliotecas](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/)
