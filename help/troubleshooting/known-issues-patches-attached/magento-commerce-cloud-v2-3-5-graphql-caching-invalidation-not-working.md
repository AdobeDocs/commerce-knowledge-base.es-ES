---
title: La invalidación del almacenamiento en caché de Adobe Commerce en la infraestructura en la nube v2.3.5 de GraphQL no funciona
description: Este artículo proporciona un parche para el problema en el que la solicitud de "GET" de GraphQL devuelve información obsoleta si el cliente cambia la información del producto.
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# La invalidación del almacenamiento en caché de Adobe Commerce en la infraestructura en la nube v2.3.5 de GraphQL no funciona

Este artículo proporciona un parche para el problema en el que la solicitud de GraphQL `GET` devuelve información obsoleta si el cliente cambia la información del producto.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube v2.3.5.

## Problema

Fastly almacena en caché las solicitudes de GraphQL y recupera la versión en caché para cada solicitud posterior de Fastly. Cuando se vuelve a guardar un producto en el backend de Adobe Commerce, la caché de Fastly debe invalidar cuando se actualiza un producto. Sin embargo, sigue siendo válido.

<u>Pasos a seguir</u>:

1. Almacene en déclencheur la siguiente solicitud de GraphQL para obtener productos para una categoría determinada como:
   <pre><magento2-server>
    </pre>
1. Vuelva a guardar uno de los productos recuperados por la solicitud anterior en el Administrador de Commerce.
1. Vuelva a almacenar en déclencheur la solicitud.

<u>Resultados esperados</u>:

El encabezado `X-Cache` contiene `MISS`.

<u>Resultados reales</u>:

El encabezado `X-Cache` contiene `HIT`, lo que significa que la respuesta se almacena en caché.

## Solución

Deshabilite la caché de productos de GraphQL con el parche que se proporciona en este artículo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en infraestructura en la nube v2.3.5

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en infraestructura en la nube v2.4.0
* Adobe Commerce local v2.4.0
* Adobe Commerce en infraestructura en la nube v2.3.5-p2
* Adobe Commerce local v2.3.5-p2
* Adobe Commerce en infraestructura en la nube v2.3.5-p1
* Adobe Commerce local v2.3.5-p1
* Adobe Commerce local v2.3.5
* Adobe Commerce en infraestructura en la nube v2.3.4-p2
* Adobe Commerce local v2.3.4-p2
* Adobe Commerce en infraestructura en la nube v2.3.4
* Adobe Commerce local v2.3.4
* Adobe Commerce local v2.3.3-p1
* Adobe Commerce local v2.3.3

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones sobre cómo aplicar un parche del compositor.

## Archivos adjuntos
