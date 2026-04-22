---
title: Correo electrónico que indica que el almacenamiento de exportaciones está casi lleno
description: Este artículo proporciona una solución para el problema en el que recibe un correo electrónico que indica que el almacenamiento de exportaciones está casi lleno.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 11cf981c7ebe813219a0cd311632eafce086bbf6
workflow-type: tm+mt
source-wordcount: '427'
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

La alerta hace referencia al sistema de archivos de almacenamiento de exportaciones, que es el volumen del disco donde se almacenan los medios y otros datos de archivo. Este sistema de archivos se monta normalmente en `/data/exports`. La alerta no indica la presencia de un solo directorio con el nombre literal de exportaciones.

Para confirmar a qué se refiere la alerta, compruebe el uso de almacenamiento de exportaciones:

* Ejecute `df -h | grep exports` y aparecerá el siguiente resultado de ejemplo:

  ```
  /dev/nvme1n1 50G 38G 12G 77% /data/exports
  tmpfs         7.7G 4.0K 7.7G  1% /data/exports/shared
  ```

* En este ejemplo, `/data/exports` es el sistema de archivos de exportaciones principal:

   * 50 GB en total
   * 38 GB utilizados
   * 12 GB disponibles (77 % de utilización)

* `/data/exports/shared` es un montaje `tmpfs` (en memoria) usado para datos compartidos y no contribuye de manera significativa a la presión del disco.

Esto confirma que la alerta se activa por el uso general del disco de `/data/exports`, no por una sola carpeta denominada exportaciones.

Si `/data/exports` muestra una alta utilización, los directorios grandes bajo este sistema de archivos (como pub/media u otras ubicaciones de archivos personalizadas) suelen ser los responsables del aumento de uso.

## Solución

Siga estos pasos para revisar, limpiar y validar el uso del almacenamiento de exportaciones.

1. Ejecute el comando `df -h | grep exports` para comprobar el uso actual del sistema de archivos de almacenamiento de exportaciones. Revise la columna **Usar%** para `/data/exports`:

   * Si el uso es del 70-85 %, empiece a planificar la limpieza.
   * Si el uso es mayor del 90 %, tome medidas inmediatamente para evitar errores de escritura o el impacto en el servicio.

1. Identifique los directorios que consumen espacio en disco significativo bajo `/data/exports` ejecutando:

   ```bash
   du -sh /data/exports/* 2>/dev/null
   ```

   Las ubicaciones típicas en las que es probable que se rellene el almacenamiento de archivos son `pub/media/catalog/product/cache` o `var/log` carpetas.

1. Limpie los archivos en función del entorno:

   * Elimine primero los archivos de exportación, los registros o los datos temporales antiguos o no utilizados.
   * En los entornos que no son de producción, normalmente puede eliminar los medios de prueba o los artefactos antiguos de forma más agresiva.
   * En entornos de producción, debe coordinarse con su equipo antes de eliminar cualquier medio o archivo esencial para el negocio.

1. Después de la limpieza, ejecute el siguiente comando `df -h | grep exports` para confirmar que el valor de **Use%** para `/data/exports` ha caído a un nivel operativo seguro.

## Lectura relacionada

[Compruebe los clústeres dedicados](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) en nuestra base de conocimiento de soporte.
