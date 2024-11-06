---
title: Los scripts personalizados del lado del servidor no se ejecutan en el directorio de medios pub
description: Este artículo proporciona una corrección para los casos en los que los scripts personalizados del lado del servidor no se ejecutan si se colocan en la etiqueta `.directorio /pub/media/` de la aplicación de Adobe Commerce en la infraestructura de la nube. Se trata de una limitación de seguridad esperada, ya que el `.El directorio /pub/media/` puede escribirse. Para que los scripts sean ejecutables, colóquelos en directorios no grabables, como `./app/code/` o `./pub/`.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Los scripts personalizados del lado del servidor no se ejecutan en el directorio de medios pub

Este artículo proporciona una corrección para los casos en los que los scripts personalizados del lado del servidor no se ejecutan si se colocan en el directorio `./pub/media/` de la aplicación de Adobe Commerce en la infraestructura en la nube. Se trata de una limitación de seguridad esperada, ya que el directorio `./pub/media/` se puede escribir. Para que los scripts sean ejecutables, colóquelos en directorios que no se puedan escribir, como `./app/code/` o `./pub/`.

## Versiones afectadas

* Adobe Commerce en la infraestructura en la nube: 2.1.x y versiones posteriores, Starter y Pro planifican la arquitectura, las arquitecturas Wings y las arquitecturas heredadas

## Problema: scripts no ejecutados

Los scripts personalizados del lado del servidor no se pueden ejecutar cuando se inician.

Por ejemplo, cuando el usuario final (comprador de Adobe Commerce) hace clic en el vínculo que lleva al archivo `\*.php` con el script (como *domain.com/media/directory/script.php* ), el script se descarga en lugar de ejecutarse.

## Causa: ubicación incorrecta del archivo de script

El problema ocurre cuando los archivos de script se encuentran en el directorio `./pub/media/` de la aplicación Adobe Commerce en la infraestructura de la nube. Este es un comportamiento esperado: debido a limitaciones de seguridad, los archivos de los directorios grabables (`./pub/media/`) nunca se ejecutan.

## Solución: coloque secuencias de comandos en directorios no grabables

Almacene los scripts del lado del servidor en directorios no grabables, como `./app/code/` o `./pub/` &quot;

## Documentación relacionada

* [Cloud for Adobe Commerce > Estructura del proyecto > Directorios editables](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories) en nuestra documentación para desarrolladores.
