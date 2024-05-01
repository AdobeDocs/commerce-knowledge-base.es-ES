---
title: "ACSD-45817: la mutación de productos de GraphQL proporciona todas las variantes configurables"
description: El parche ACSD-45817 corrige el problema en el que una mutación "products" de GraphQL para un almacén específico devuelve todas las variantes configurables, incluidas las que no están asignadas al almacén solicitado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. El ID del parche es ACSD-45817. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.
exl-id: 3d61d1aa-36b5-471d-929b-7df8ce65c791
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-45817: la mutación de productos de GraphQL proporciona todas las variantes configurables

El parche ACSD-45817 corrige el problema en el que un GraphQL `products` La mutación de un almacén específico devuelve todas las variantes configurables, incluidas las que no están asignadas al almacén solicitado. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalado. El ID del parche es ACSD-45817. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

A GRAPHQL `products` La mutación de un almacén específico devuelve todas las variantes configurables, incluidas las que no están asignadas al almacén solicitado.

<u>Requisitos previos</u>:

Cree un segundo sitio web, una segunda tienda y una segunda vista de la tienda.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con dos subproductos: &quot;configurable-a&quot; y &quot;configurable-b&quot;.
1. Asigne el producto configurable a ambos sitios web.
1. Asigne solo una variación &quot;configurable-a&quot; al segundo sitio web.
1. Vaya a la **Tienda**, cambie al segundo sitio web y abra el producto configurable.
1. Asegúrese de ver solo una opción secundaria: &quot;configurable-a&quot;.
1. Ejecutar una consulta de GraphQL mediante `POST: /graphql` extremo, y `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>Resultados esperados</u>:

La variación &quot;configurable-b&quot; no está asignada al segundo sitio web y no debe mostrarse en la respuesta.

<u>Resultados reales</u>:

La variación &quot;configurable-b&quot; se muestra en la respuesta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
