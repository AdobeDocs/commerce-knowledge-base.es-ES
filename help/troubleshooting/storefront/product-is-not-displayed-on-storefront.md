---
title: El producto no se muestra en la tienda
description: Este artículo proporciona soluciones para los casos en los que los productos no se muestran en la tienda.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '327'
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
1. Vaya a **Catálogo** > **Productos**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Haga clic en **Agregar producto** y continúe con el proceso de creación del producto. O importe productos desde un archivo CSV.

<u>Resultado esperado</u>:

El producto se muestra en la tienda.

<u>Resultado real</u>:

El producto no se muestra.

## Causa

Esto puede deberse a varias razones. Siga los pasos a continuación para comprobar los puntos principales que pueden ayudar a identificar y resolver el problema.

## Solución

Cada uno de los siguientes puntos puede resolver el problema.

* Compruebe la configuración del producto en Administración. Vaya a **Catálogo** > **Productos**, abra la página del producto y asegúrese de que los campos siguientes estén correctamente configurados:
  * **Habilitar producto** = *Sí.*
  * **Estado de stock**: *En stock*. O si *Sin existencias* es el valor correcto, asegúrese de que **Mostrar productos sin existencias** (**TIENDAS** > **Configuración** > **Configuración** > **CATÁLOGO** > **Inventario** > **Opciones de existencias** > **Mostrar productos sin existencias**) esté establecido en *Sí* (configurado a nivel global).
  * **Categorías**: si intenta encontrar el producto en una página de categoría, compruebe que el producto esté asignado a la categoría. Para simplificar la resolución de problemas, cree una nueva categoría desde la página actual y asígnele un producto.
  * **Visibilidad** = *Catálogo, búsqueda.*
  * En la sección **Producto en sitios web**, asegúrese de que el producto esté asignado al sitio web correcto.
  * Cambie el selector de ámbito a la vista de tienda donde intenta encontrar el producto en la tienda y compruebe la misma configuración.
* Realice el reindexado completo, ejecutando `bin/magento indexer:reindex` desde la consola, y vacíe toda la caché en el administrador, en **Sistema** > **Herramientas** > **Administración de caché**, o desde la consola ejecutando `bin/magento cache:clean`.
* Si lo anterior no ayuda, puede iniciar una investigación adicional comprobando los registros en el directorio `var/log`.



