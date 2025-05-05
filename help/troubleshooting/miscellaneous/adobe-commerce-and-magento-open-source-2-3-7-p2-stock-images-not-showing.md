---
title: Imágenes de archivo no mostradas, Adobe Commerce y Magento Open Source 2.3.7-p2
description: Este artículo proporciona una solución al problema de que las imágenes de stock de Adobe cargadas en los directorios del sistema de archivos "pub/media" o "pub/media/catalog" no se muestran en la interfaz de usuario de Media Gallery. Esto se debe a que las imágenes están fuera de los directorios de galería de medios permitidos. Para que estas imágenes se muestren a los comerciantes, deben eliminarlas en el sistema de archivos y volver a cargarlas en un directorio de Media Gallery permitido.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Imágenes de archivo no mostradas, Adobe Commerce y Magento Open Source 2.3.7-p2

Este artículo proporciona una solución para el problema en el que las imágenes de existencias de Adobe cargadas en los directorios del sistema de archivos `pub/media` o `pub/media/catalog` no se muestran en la interfaz de usuario de Media Gallery. Esto se debe a que las imágenes están fuera de los directorios de galería de medios permitidos. Para que estas imágenes se muestren a los comerciantes, deben eliminarlas en el sistema de archivos y volver a cargarlas en un directorio de Media Gallery permitido.

## Productos y versiones afectados

* Adobe Commerce y Magento Open Source 2.3.7-p2


## Problema

Los comerciantes pueden cargar imágenes de Adobe Stock en la raíz del almacenamiento de la Galería de medios, pero estas imágenes no aparecen en la interfaz de usuario y aparecerán como si no se hubieran cargado. Esto se debe a que el sistema observa que la imagen ya se ha cargado en el sistema de archivos, aunque no está disponible en la interfaz de usuario de Media Gallery. Esto significa que una vez que un comerciante carga una imagen en `pub/media` o `pub/media/catalog`, no puede usarla hasta que se elimine directamente en el sistema de archivos.

<u>Pasos a seguir</u>

1. Habilite Adobe Stock con claves de API válidas.
1. Abra la galería de medios (**Catálogo** > **Categorías** > **Contenido** sección > haga clic en **Seleccionar de la galería**).
1. Haga clic en **Buscar en Adobe Stock**.
1. Seleccione una imagen. Haga clic en **Guardar vista previa**. Tenga en cuenta que es posible que tenga que restablecer la cuadrícula de Adobe Stock para que aparezcan las imágenes.

<u>Resultado esperado</u>:

Se muestra la imagen.

<u>Resultado real</u>:

Aparece un mensaje de error: *No se encuentra la imagen. No se puede encontrar esta imagen en la galería de medios.*

## Causa

Las imágenes se pueden cargar a la raíz de almacenamiento de la Galería multimedia mediante Adobe Stock.

## Solución

Seleccione cualquier subdirectorio de la raíz de almacenamiento de Media Gallery (excluyendo **Raíz de almacenamiento** > **Catálogo**) antes de cargar una imagen de Adobe Stock.
Elimine las imágenes de Adobe Stock cargadas de las carpetas `pub/media` y `pub/media/catalog` del sistema de archivos de Adobe Commerce y, en su lugar, cargue las imágenes en cualquier subdirectorio raíz de almacenamiento de Media Gallery permitido (excluyendo **Raíz de almacenamiento** > **Catálogo**).

## Lectura relacionada

* [Almacenamiento de medios](https://experienceleague.adobe.com/es/docs/commerce-admin/content-design/wysiwyg/storage/media-storage) en nuestra guía del usuario.
