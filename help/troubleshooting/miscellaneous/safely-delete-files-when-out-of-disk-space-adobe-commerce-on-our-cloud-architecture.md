---
title: Elimine archivos de forma segura cuando el disco se quede sin espacio en Adobe Commerce en la infraestructura en la nube
description: Este artículo proporciona una solución para cuando se queda sin espacio en disco y necesita quitar archivos de forma segura. Antes de considerar esta acción, revise [Administrar espacio en disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html#no-space-left) en nuestra documentación para desarrolladores. Si los pasos de ese artículo no son adecuados para usted o no resuelven el problema, revise los pasos de este artículo.
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 86515936f72bbd0a5778cb81f665993ed91e4707
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Elimine archivos de forma segura cuando el disco se quede sin espacio en Adobe Commerce en la infraestructura en la nube

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.2 - 2.4.7
* Esto es específico de los clústeres Pro dedicados. Los entornos de Inicio e Integración son de un solo nodo y no tienen el `/data/exports` directorio.

## Signos de poco espacio en disco

Las señales de que se está quedando sin espacio en disco pueden ser una implementación atascada, advertencias de llenado de disco y un rendimiento deficiente.
Para ver la cantidad de espacio en disco que utiliza el sistema de archivos, ejecute el siguiente comando en CLI/Terminal:

`df -h`


## Cómo eliminar archivos de forma segura para aumentar el espacio en disco

Puede eliminar archivos de los puntos de montaje de la aplicación, desde su `/app` ruta o pasante `/mnt/shared`. Existen dos formas diferentes de acceder a los mismos archivos.

>[!WARNING]
>
>**Nunca modifique ni elimine el contenido de`/data/exports`**.
>
>`/data/exports` es el almacenamiento subyacente detrás del sistema de archivos compartido, y es administrado por GlusterFS.
>
>El sistema de archivos contiene no solo el contenido del archivo, sino también metadatos sobre el estado del sistema de archivos para permitir la sincronización >entre los nodos del clúster. **Cambiar o eliminar archivos directamente dentro de este sistema de archivos dañará el sistema de archivos compartido, requiriendo reparaciones extensas o recuperación de datos.**

Para localizar los archivos más grandes que puedan ser buenos candidatos para borrar, ejecute el siguiente comando (en proyectos grandes o ocupados puede tardar hasta una hora):

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

La salida del comando contendrá una lista de los archivos y directorios más grandes con sus tamaños especificados.

## Lectura relacionada

En nuestra base de conocimiento de soporte:

* [Aumente el espacio en disco para el entorno de integración en la nube](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [Poco espacio en disco](/help/troubleshooting/miscellaneous/low-disk-space.md)

En nuestra documentación para desarrolladores:

* [Administrar espacio en disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html)
