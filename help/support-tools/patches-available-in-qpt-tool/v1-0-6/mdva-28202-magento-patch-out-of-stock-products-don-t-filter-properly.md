---
title: "Parche MDVA-28202: los productos sin existencias no filtran correctamente"
description: El parche MDVA-28202 soluciona el problema de que los productos sin existencias no se filtran correctamente mediante el filtro **Precio** en el front-end de una tienda Adobe Commerce. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6.
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Parche MDVA-28202: los productos sin existencias no filtran correctamente

El parche MDVA-28202 soluciona el problema de que los productos sin existencias no se filtran correctamente usando el filtro **Price** en el front-end de una tienda Adobe Commerce. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6.

## Productos y versiones afectados

* El parche se ha diseñado para Adobe Commerce en la infraestructura en la nube 2.3.5-p1.
* El parche también es compatible con Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.4 - 2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos sin existencias no filtran correctamente usando el filtro **Price** en el administrador de Commerce.

<u>Requisito previo:</u>

* Definir **Mostrar productos sin existencias** = &quot;*Sí*&quot; en **Tiendas > Configuración > CATÁLOGO > Inventario > Opciones de existencias**.

<u>Pasos a seguir:</u>

1. Cree un producto configurable con dos productos simples (Ejemplo: set **Price** = *$1500*).
1. Los dos productos simples deben estar &quot;agotados&quot; al crear el producto configurable.
1. Asigne este producto configurable a una categoría.
1. Reindexe y compruebe la tabla `catalog_product_index_price` mediante el ID de entidad del producto configurable anterior.
1. Guardar todos los precios del producto = *$0*.
1. Cargue la categoría y confirme la disponibilidad del producto.
1. Abra el filtro **Price** desde la navegación por capas.
1. Observe que el filtro **Price** tiene una opción de &quot;*$0.00 - $9.99*&quot;.
1. Haz clic en esta opción de filtro superior de **Precio** y establece el **Precio** = *$1500*, y obtendrás el producto configurable que hemos creado anteriormente.

<u>Resultado esperado:</u>

El producto filtra bajo el rango de precios correcto según lo esperado.

<u>Resultado real:</u>

El producto se encuentra en un filtro de rango de precios incorrecto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del método de implementación:

* Adobe Commerce o Magento Open Source local: [Aplique parches con la herramienta de parches de calidad](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

Para obtener más información sobre los productos configurables, consulte este artículo en nuestra documentación para desarrolladores: [Crear un tutorial configurable de producto](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) en nuestra documentación para desarrolladores.
