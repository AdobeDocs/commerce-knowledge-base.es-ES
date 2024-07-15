---
title: "Adobe Commerce local 2.4.2: falta la imagen del producto"
description: Este artículo describe un problema conocido de la versión 2.4.2 local de Adobe Commerce en el que la imagen del producto no se carga en la página del producto. Está previsto que este problema se resuelva en una versión futura posterior a la 2.4.3. No hay una solución disponible en este momento, pero como solución alternativa, puede deshabilitar Nginx para cambiar el tamaño de las imágenes.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce local 2.4.2: falta la imagen del producto

Este artículo describe un problema conocido de la versión 2.4.2 local de Adobe Commerce en el que la imagen del producto no se carga en la página del producto. Está previsto que este problema se resuelva en una versión futura posterior a la 2.4.3. No hay una solución disponible en este momento, pero como solución alternativa, puede deshabilitar Nginx para cambiar el tamaño de las imágenes.

## Productos y versiones afectados

* Adobe Commerce local 2.4.2

## Problema

La imagen del producto se guardó en el bloque `s3`, pero no se sincronizó con el directorio `pub/media`. Este problema solo se produce cuando se utilizan ambos:

* Nginx habilitado para el sitio para cambiar el tamaño de las imágenes
* AWS `s3` como almacenamiento de medios

<u>Requisitos previos</u>:

Adobe Commerce instalado con Nginx.

<u>Pasos a seguir</u>:

1. Configure Adobe Commerce para que use AWS `s3` como almacenamiento de medios.
1. Configure Nginx usando el archivo de configuración `nginx.conf.sample` proporcionado en el directorio de instalación de Adobe Commerce y un host virtual Nginx. Consulte [Configurar Nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html#configure-nginx-ubuntu) en nuestra documentación para desarrolladores.
1. Cree un producto sencillo con una imagen de producto.
1. Nginx tiene una configuración sin comentarios para el cambio de tamaño de la imagen en `nginx.conf.sample` similar a esta:

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>Resultados esperados</u>:

La imagen del producto se carga en la página del producto.

<u>Resultados reales</u>:

La imagen del producto no se ha cargado a la página del producto.

## Solución

Deshabilite Nginx para cambiar el tamaño de las imágenes.
