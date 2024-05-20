---
title: "Correo electrónico que indica que el almacenamiento de exportaciones está casi lleno"
description: Este artículo proporciona una solución para el problema en el que recibe un correo electrónico que indica que el almacenamiento de exportaciones está casi lleno.
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Correo electrónico que indica que el almacenamiento de exportaciones está casi lleno

Este artículo proporciona una solución para el problema en el que recibe un correo electrónico que indica que el almacenamiento de exportaciones está casi lleno.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Problema

Recibirá un correo electrónico con el siguiente contenido, pero no podrá localizar el *exportaciones* carpeta:

*Nuestro monitoreo ha detectado que el almacenamiento de &#39;exportaciones&#39; en su clúster XXX está lleno en torno al &#39;85%&#39;.*
*Si es necesario, revise el uso, realice una limpieza o solicite un aumento.*
*Además, tenga en cuenta que intentaremos un aumento de tamaño automáticamente cuando el almacenamiento alcance el nivel de umbral crítico.*

## Causa

El correo electrónico hace referencia a **exportaciones** almacenamiento, que es la cantidad de disco asignada a los archivos o medios, y no una carpeta específica denominada *exportaciones*.

## Solución

Debe revisar el uso de archivos en el entorno. Ejecute este comando para obtener el uso existente:

`df -h |grep data`

Las ubicaciones típicas donde es probable que se rellene el almacenamiento de archivos son las siguientes *pub/media/catalog/product/cache* o *var/log* carpetas. Para determinar el espacio en disco utilizado por los archivos, ejecute este comando con la ruta de acceso adecuada */path/to/folder*:

`du -shc` */path/to/folder*

Si el uso del disco de medios constituye una gran proporción del espacio total en disco, quizá le interese habilitar [Optimización de imagen muy profunda](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)y, a continuación, elimine los archivos en la *pub/media/catalog/product/cache* carpeta en el servidor manualmente.

## Lectura relacionada

[Comprobar clústeres dedicados](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) en nuestra base de conocimiento de soporte.