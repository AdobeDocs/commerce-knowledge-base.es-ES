---
title: "MDVA-37748: La consulta de GraphQL devuelve productos no asignados al catálogo compartido"
description: El parche MDVA-37748 corrige el problema en el que una consulta de GraphQL devuelve productos no asignados a un catálogo compartido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5. El ID del parche es MDVA-37748. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 1f441882-dc14-433c-aa03-ff22483ce5a7
feature: B2B, GraphQL, Catalog Management, Categories, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# MDVA-37748: La consulta de GraphQL devuelve productos no asignados al catálogo compartido

El parche MDVA-37748 corrige el problema en el que una consulta de GraphQL devuelve productos no asignados a un catálogo compartido. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5 está instalado. El ID del parche es MDVA-37748. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta de GraphQL devuelve productos no asignados a un catálogo compartido.

<u>Requisitos previos</u>:

Los módulos B2B están instalados.

<u>Pasos a seguir</u>:

1. Cree dos productos y asígnelos a una categoría:
   * Producto 1 - Público
   * Product 2

1. Asigne &quot;Product 1 - Public&quot; al catálogo compartido &quot;Default (General)&quot;.
1. Cree un catálogo compartido personalizado adicional y asígnelo a &quot;Producto 2&quot;.
1. Cree una nueva compañía y asígnela al catálogo compartido adicional creado en el paso tres.
1. Después de la ejecución/reindexación de cron, en el front-end, valide que puede ver &quot;Producto 1: público&quot; si no ha iniciado sesión.
1. Inicie sesión como administrador de la compañía creada en el paso 4 y compruebe que solo ve el producto 2.
1. Solicite un token de autorización con la siguiente consulta de GraphQL:

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(
        email: "company.admin@exapmle.test"
        password: "password"
      ) {
        token
      }
    }
    </code>
    </pre>

1. Añadir encabezado **Valor del token del portador de autorización** y ejecute la siguiente consulta de GraphQL:

   <pre>
    <code class="language-graphql">
    {
      products(
          filter: {},
          pageSize: 100,
          currentPage: 1
          sort: {}
        ) {
          total_count
          page_info {
            page_size
            current_page
          }
          aggregations {
            attribute_code
            count
            label
            options {
              label
              value
              count
            }
          }
          items {
            name
            sku
            created_at
            updated_at
            stock_status
            description {html}
            short_description {html}
            url_key
            url_path
            price_tiers{
              final_price{
                  value
                  currency
                }
              discount{
                  amount_off
                  percent_off
                }
              quantity
            }
            price_range {
             maximum_price {
              regular_price {
                value
              }
              final_price {
                value
              }
            }
            minimum_price {
              regular_price {
                value
              }
              final_price {
               value
              }
            }
          }
          image {
           url
          }
          thumbnail {
           url
          }
          small_image {
           url
          }
          media_gallery {
           url
          }
          ... on ConfigurableProduct {
            configurable_options {
             id

             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
               swatch_data {
                 value
               }
            }
            product_id
          }
          variants {
            product {
              id
              name
              sku
              #margin
              #margin_percentage
              image {
                url
              }
              small_image {
                url
              }
              thumbnail {
                url
              }
              media_gallery{
                url
              }
              attribute_set_id
              ... on PhysicalProductInterface {
                weight
              }
              price_range {
                minimum_price {
                  regular_price {
                    value
                    currency
                  }
                }
              }
            }
            attributes {
              label
              code
              value_index
            }
          }
        }
      }

    }
}
</code>
</pre>

<u>Resultados esperados</u>:

El recuento y el producto devueltos por GraphQL solo tienen en cuenta el producto asignado al catálogo compartido asociado al usuario que ha iniciado sesión.

<u>Resultados reales</u>:

Solo se devuelve &quot;Product 2&quot;, pero el `total_count` muestra dos.

<pre>
<code class="language-graphql">
{
  "data": {
    "products": {
      "total_count": 2,
      "page_info": {
        "page_size": 100,
        "current_page": 1
      },
      "aggregations": [
        {
          "attribute_code": "price",
          "count": 2,
          "label": "Price",
          "options": [
            {
              "label": "0-100",
              "value": "0_100",
              "count": 1
            },
            {
              "label": "100-200",
              "value": "100_200",
              "count": 1
            }
          ]
        },
        {
          "attribute_code": "category_id",
          "count": 1,
          "label": "Category",
          "options": [
            {
              "label": "Cat 1",
              "value": "3",
              "count": 2
            }
          ]
        }
      ],
      "items": [
        {
          "name": "Product 2",
          "sku": "Product 2",
          "created_at": "2021-05-12 10:51:44",
          "updated_at": "2021-05-12 11:03:24",
          "stock_status": "IN_STOCK",
          "description": {
            "html": ""
          },
          "short_description": {
            "html": ""
          },
          "url_key": "product-2",
          "url_path": null,
          "price_tiers": [
            {
              "final_price": {
                "value": 90,
                "currency": "USD"
              },
              "discount": {
                "amount_off": 10,
                "percent_off": 10
              },
              "quantity": 1
            }
          ],
          "price_range": {
            "maximum_price": {
              "regular_price": {
                "value": 100
              },
              "final_price": {
                "value": 90
              }
            },
            "minimum_price": {
              "regular_price": {
                "value": 100
              },
              "final_price": {
                "value": 90
              }
            }
          },
          "image": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/image.jpg"
          },
          "thumbnail": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/thumbnail.jpg"
          },
          "small_image": {
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/small_image.jpg"
          },
          "media_gallery": []
        }
      ]
    }
  }
}
</code>
</pre>

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
