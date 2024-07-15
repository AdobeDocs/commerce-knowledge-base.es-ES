---
title: "MDVA-40488: Los productos configurables con productos secundarios agotados no se muestran en el rango de precios correcto"
description: El parche MDVA-40488 resuelve el problema en el que los productos configurables con productos secundarios agotados no se muestran en su rango de precios correcto. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-40488. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: los productos configurables con productos secundarios agotados no se muestran en el rango de precios correcto

El parche MDVA-40488 resuelve el problema en el que los productos configurables con productos secundarios agotados no se muestran en su rango de precios correcto. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-40488. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos configurables con productos secundarios agotados no se muestran en su rango de precios correcto.

<u>Requisitos previos</u>:

Vaya a Commerce Admin > **tiendas** > **configuración** > **catálogo** > **Inventario** > **opciones de stock** y establezca la configuración de **Mostrar productos sin existencias** en *Sí*.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con dos productos asociados. Por ejemplo: productos simples rojo y marrón.
1. Establezca el inventario del producto simple en Rojo, establezca el estado de stock en *En stock* y, a continuación, establezca el estado Habilitar producto en *No*.
1. Establezca el inventario del producto simple Marrón y, a continuación, establezca el estado Habilitar producto en *Sí*.
1. Asegúrese de que el estado de Stock del producto configurable sea *En Stock*.
1. Cambie el inventario del producto simple Marrón a 0 y establezca el estado de las existencias en *Agotado*.
1. En este punto, el estado de stock del producto configurable sigue siendo *En stock*.
1. Realice una reindexación.
1. Compruebe `min_price` y `max_price` para el producto configurable en la tabla de base de datos `catalog_product_index_price`; los dos valores se establecen en 0.
1. Pero si establecemos el estado de stock del producto configurable en *Agotado* y reindexamos, podemos ver valores distintos de cero de `min_price` y `max_price` del producto configurable.

<u>Resultados esperados</u>:

Si todos los productos secundarios están *Agotados* y el producto configurable en sí también está *Agotados*, el precio se calcula usando todos los productos secundarios.

<u>Resultados reales</u>:

Los valores `min_price` y `max_price` del producto configurable en la tabla de base de datos `catalog_product_index_price` se establecen en 0 cuando el estado de existencias configurable es *En existencias*, pero si es *Sin existencias*, se convierten en valores distintos de cero.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
