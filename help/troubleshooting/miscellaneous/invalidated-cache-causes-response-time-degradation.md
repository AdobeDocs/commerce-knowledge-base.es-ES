---
title: La caché no validada provoca una degradación del tiempo de respuesta
description: Este artículo proporciona una solución sobre cómo evitar la invalidación de la caché, que puede causar el bajo rendimiento de una tienda Adobe Commerce.
exl-id: 7cb6a39f-923b-4acc-965d-23cf7b52c25a
feature: Cache, Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# La caché no validada provoca una degradación del tiempo de respuesta

Este artículo proporciona una solución sobre cómo evitar la invalidación de la caché, que puede causar el bajo rendimiento de una tienda Adobe Commerce.

PRODUCTOS Y VERSIONES AFECTADOS:

* Adobe Commerce local 2.2.x, 2.3.x
* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x

## Problema

Respuesta lenta del sitio.

## Causa

El tiempo de respuesta largo puede deberse a que la caché se invalida (se vacía).

La caché se utiliza para generar respuestas rápidas a las solicitudes de los visitantes del sitio. Si no hay datos de caché adecuados disponibles, la aplicación de Adobe Commerce recupera los datos de la base de datos, calcula y agrega los datos y los almacena en el almacenamiento de caché. El proceso de generación de caché requiere recursos de sistema adicionales, lo que provoca una degradación total del tiempo de respuesta.

Hay dos tipos de caché en Adobe Commerce:

1. Interno:
   * almacena datos en el servidor
   * almacena datos específicos (configuración, detalles del producto, detalles de la categoría, etc.)
1. Externo:
   * CDN o Varnish (en el caso de Adobe Commerce en la infraestructura en la nube, Fastly CDN)
   * almacena páginas completas ya generadas. Por ejemplo: páginas de catálogo/categoría, páginas de catálogo/producto, etc.

### Compruebe si ha invalidado la caché

Puede encontrar información sobre los tipos de caché invalidados en el archivo `<install_directory>/var/log/debug.log`.

Para ello:

1. Abrir `<install_directory>/var/log/debug.log`
1. Busque el mensaje &quot; *cache\_invalidate*&quot;.
1. A continuación, compruebe la etiqueta especificada. Indica qué caché se vació. Es posible que tenga problemas debido a la caché invalidada si ve una etiqueta sin un ID de entidad en particular especificado, por ejemplo:
   * `cat_p`: significa caché de producto de catálogo.
   * `cat_c` - caché de categoría de catálogo.
   * `FPC` - caché de página completa.
   * `CONFIG` - caché de configuración.

   Tener incluso uno de ellos vaciado ralentizaría la respuesta del sitio web. Si la etiqueta contiene un id de entidad, por ejemplo, `category_product_1258`, esto indicaría la caché de un producto o categoría en particular, etc. El vaciado de la caché de un producto o categoría en particular no haría que el tiempo de respuesta disminuyera significativamente.

A continuación se muestra un ejemplo de un(a) `debug.log` que contiene registros que indican que se ha vaciado la caché de `cat_p` y `category_product_15044`:

![muestra del contenido debug.log](assets/debug_log_sample.png)

Normalmente, la caché se invalida debido a lo siguiente:

* Reindexación completa.
* Caché parpadeante desde CLI, ya sea manualmente o mediante cron.

## Recomendación

1. Evite vaciar la caché de la CLI de Commerce.
1. Configure los indexadores a **Actualizar mediante programación** en lugar de **Actualizar en el modo de guardado** porque este último déclencheur la reindexación completa. Como referencia, consulte [Administrar los indexadores > Configurar indexadores](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) en nuestra documentación para desarrolladores.
