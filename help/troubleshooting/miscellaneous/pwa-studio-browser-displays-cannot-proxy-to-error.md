---
title: '"PWA Studio: El explorador muestra "No se puede proxy al"error"'
description: En este tema se describe una solución cuando el explorador web muestra "*No se puede proxy a*" y la consola muestra un
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio: El explorador muestra el error &quot;No se puede proxy a&quot;.

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

* [PWA Studio para la documentación de Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Herramientas y bibliotecas](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
