---
title: El producto no se muestra en la tienda
description: Este artículo proporciona soluciones para los casos en los que los productos no se muestran en la tienda.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# El producto no se muestra en la tienda

Este artículo proporciona soluciones para los casos en los que los productos no se muestran en la tienda.

## Productos y versiones afectados

* Adobe Commerce local X.X.X
* Adobe Commerce en infraestructura en la nube X.X.X

## Problema

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de Commerce.
1. Ir a **Catálogo** > **Productos**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Clic **Añadir producto** y pasar por el proceso de creación del producto. O importe productos desde un archivo CSV.

<u>Resultado esperado</u>:

El producto se muestra en la tienda.

<u>Resultado real</u>:

El producto no se muestra.

## Causa

Esto puede deberse a varias razones. Siga los pasos a continuación para comprobar los puntos principales que pueden ayudar a identificar y resolver el problema.

## Solución

Cada uno de los siguientes puntos puede resolver el problema.

* Compruebe la configuración del producto en Administración. Ir a **Catálogo** > **Productos**, abra la página del producto y asegúrese de que los siguientes campos están correctamente configurados:
   * **Activar producto** = *Sí.*
   * **Estado de stock**: *En stock*. O si *Sin existencias* es el valor correcto, asegúrese de que **Mostrar productos sin existencias** (**TIENDAS** > **Configuración** > **Configuración** > **CATÁLOGO** > **Inventario** > **Opciones de Stock** > **Mostrar productos sin existencias**) se ha definido en *Sí* (configurado a nivel global).
   * **Categorías**: si intenta encontrar el producto en una página de categoría, compruebe que el producto esté asignado a la categoría. Para simplificar la resolución de problemas, cree una nueva categoría desde la página actual y asígnele un producto.
   * **Visibilidad** = *Catálogo, Buscar.*
   * En el **Producto en sitios web** , asegúrese de que el producto está asignado al sitio web correcto.
   * Cambie el selector de ámbito a la vista de tienda donde intenta encontrar el producto en la tienda y compruebe la misma configuración.
* Realice la reindexación completa ejecutando `bin/magento indexer:reindex` de la consola y vacíe toda la caché de la Admin, en **Sistema** > **Herramientas** > **Administración de caché**, o desde la consola ejecutando `bin/magento cache:clean`.
* Si lo anterior no ayuda, puede iniciar una investigación adicional comprobando los registros en la `var/log` directorio.

## Lectura relacionada en nuestra base de conocimiento de soporte

* [Ubicaciones de registro (directorios) para la arquitectura Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [Ubicaciones de registro (directorios) para la arquitectura de inicio](/help/how-to/general/log-locations-directories-for-starter-plan.md)
