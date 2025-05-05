---
title: Correo electrónico que indica que el almacenamiento de exportaciones está casi lleno
description: Este artículo proporciona una solución para el problema en el que recibe un correo electrónico que indica que el almacenamiento de exportaciones está casi lleno.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Correo electrónico que indica que el almacenamiento de exportaciones está casi lleno

Este artículo proporciona una solución para el problema en el que recibe un correo electrónico que indica que el almacenamiento de exportaciones está casi lleno.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Problema

Recibió un correo electrónico con el siguiente contenido, pero no pudo encontrar la carpeta *exports*:

*Nuestra supervisión ha detectado que el almacenamiento de &#39;exportaciones&#39; en su clúster XXX está lleno en torno al &#39;85%&#39;.*
*Si es necesario, revise el uso, realice una limpieza o solicite una ampliación.*
*Tenga en cuenta también que intentaremos aumentar el tamaño automáticamente cuando el almacenamiento alcance el nivel de umbral crítico.*

## Causa

El correo electrónico hace referencia al almacenamiento de **exports**, que es la cantidad de disco asignado a los archivos o medios, y no a una carpeta específica denominada *exports*.

## Solución

Debe revisar el uso de archivos en el entorno. Ejecute este comando para obtener el uso existente:

`df -h |grep data`

Las ubicaciones típicas donde es probable que se rellene el almacenamiento de archivos son las carpetas *pub/media/catalog/product/cache* o *var/log*. Para determinar el espacio en disco utilizado por los archivos, ejecute este comando con la ruta de acceso apropiada */path/to/folder*:

`du -shc` */ruta/a/carpeta*

Si el uso del disco multimedia constituye una gran proporción del espacio total en el disco, quizá quiera habilitar [Optimización de imagen profunda rápida](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization) y, a continuación, eliminar manualmente los archivos de la carpeta *pub/media/catalog/product/cache* en el servidor.

## Lectura relacionada

[Compruebe los clústeres dedicados](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) en nuestra base de conocimiento de soporte.
