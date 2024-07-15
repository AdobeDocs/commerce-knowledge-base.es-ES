---
title: Las imágenes de producto no se muestran a pesar de las funciones de imagen de edición de producto
description: Este artículo proporciona una corrección para los casos en los que las imágenes de producto no se muestran en la tienda, a pesar de las funciones de imagen establecidas en la página Editar producto.
exl-id: 456baa5a-fa16-4bc1-9d6c-54106fae58ca
feature: Cache, Products, Roles/Permissions, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Las imágenes de producto no se muestran a pesar de las funciones de imagen de edición de producto

Este artículo proporciona una corrección para los casos en los que las imágenes de producto no se muestran en la tienda, a pesar de las funciones de imagen establecidas en la página Editar producto.

**Causa:** en instancias de Adobe Commerce con más de un almacén, algunas imágenes de producto pueden tener los valores `no_selection` para los atributos de función de imagen `image`, `small_image`, `thumbnail`, `swatch`. Estos `no_selection` valores surgen cuando la función de imagen del producto se establece en el ámbito global de todas las tiendas en lugar del ámbito de una tienda en particular (es decir, en **Todas las vistas de la tienda** en lugar de en una **vista de la tienda** en particular). Para saber si ese es su caso, ejecute el script SQL desde la sección **Causa** a continuación.

**Solución:** elimine filas con los valores `no_selection` para estas imágenes usando el script SQL de la sección Solución a continuación.

## Versiones afectadas

* Adobe Commerce local 2.X.X
* Adobe Commerce en infraestructura en la nube 2.X.X

## Problema

Es posible que las imágenes del producto no se muestren en la tienda, aunque las funciones de imagen (Base, Pequeña, Miniatura, Muestra) se hayan configurado correctamente en la página Producto del panel de administración.

Al comprobar la página de productos con **Vista de la tienda** establecida en **Todas las vistas de la tienda**, la imagen tiene las funciones establecidas en la pantalla **Detalle de la imagen**.

![todas_las_vistas_tienda.png](assets/all_store_views.png)

![image_roles.png](assets/image_roles.png)

Sin embargo, en la tienda, la imagen no aparece; cuando marca la página del producto en el nivel de tienda en particular (cambiando la **vista de la tienda**), la imagen está allí, pero los roles no están establecidos.

![image_roles_not_set.png](assets/image_roles_not_set.png)

## Causa

En las instancias de Adobe Commerce de varias tiendas (con más de un almacén), algunas imágenes de producto pueden tener los valores `no_selection` para los atributos `image`, `small_image`, `thumbnail`, `swatch` (estos atributos corresponden a funciones de imagen). Estos `no_selection` valores surgen cuando la función de imagen del producto se establece en el ámbito global de todas las tiendas en lugar del ámbito de una tienda en particular (es decir, en **Todas las vistas de la tienda** en lugar de en una **vista de la tienda** en particular).

Técnicamente hablando: en `store_id=0` (que contiene la configuración global de todas las tiendas en su instancia de Adobe Commerce), se pueden establecer las funciones de imagen del producto: esto significa que los atributos `image`, `small_image`, `thumbnail`, `swatch` tienen valores válidos (ruta de acceso a las imágenes). Al mismo tiempo, en `store_id=1` (que es una representación de almacén en particular), los valores de estos atributos son `no_selection`.

### Cómo verificar que ese es su problema

Ejecute esta consulta SQL:

```sql
SELECT `cpev_s`.*, `cpev_0`.`value` AS `store_value` FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Si la consulta devuelve un resultado como el siguiente, está tratando el problema documentado en este artículo:

```sql
+----------+--------------+----------+--------+--------------+----------------------------+
| value_id | attribute_id | store_id | row_id | value        | store_value                |
+----------+--------------+----------+--------+--------------+----------------------------+
|    67722 |           87 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67723 |           88 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67724 |           89 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67814 |           87 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6769 |           87 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67815 |           88 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6770 |           88 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67816 |           89 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6771 |           89 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
+----------+--------------+----------+--------+--------------+----------------------------+
9 rows in set (0.06 sec)
```

### ¿Por qué ocurre esto?

Si la aplicación Adobe Commerce tiene más de un almacén, no se pueden sincronizar datos entre un almacén en particular y la configuración del almacén global.

Los valores de `store_id=1` tienen más prioridad que el almacén predeterminado (global) (`store_id=0`). Por lo tanto, la aplicación puede omitir la configuración de imagen global y usar la configuración de ámbito de almacenamiento (`no_selection` para los atributos de función de imagen) al mostrar una imagen.

## Solución {#solution}

Eliminar atributos con los valores `no_selection` mediante este script SQL:

```
DELETE `cpev_s`.* FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

Una vez eliminados estos atributos, se establecen las funciones de tiendas concretas y se muestran las imágenes en la tienda.

## Detalles adicionales

No podrá ver los resultados de la corrección inmediatamente si Caché de página completa está habilitada en la instancia de Adobe Commerce.

Para que se muestren los cambios, actualice la caché de la página con el menú **Administración de caché** del panel de administración.

## Más información

### Almacenes y ámbitos

[Almacena y almacena ámbitos](/docs/commerce-admin/stores-sales/site-store/stores.html) en nuestra guía de usuario

### Imágenes

[Cargando imágenes de productos](/docs/commerce-admin/catalog/products/digital-assets/product-image.html#upload-an-image) en nuestra guía de usuario

### Caché

* [Administración de caché](/docs/commerce-admin/systems/tools/cache-management.html) en nuestra Guía del sistema de administración de usuarios.
* [Administrar la caché](/docs/commerce-operations/configuration-guide/cli/manage-cache.html) en nuestra documentación para desarrolladores