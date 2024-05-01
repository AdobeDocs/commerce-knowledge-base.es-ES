---
title: "MDVA-37288: Precios de nivel incorrectos devueltos tras la solicitud de GraphQL"
description: El parche de calidad MDVA-37288 para Adobe Commerce soluciona el problema de devolver precios de nivel incorrectos tras una solicitud de GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.
exl-id: d2cf24d5-6163-4968-a89c-b7407d439e1c
feature: GraphQL, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-37288: Precios de nivel incorrectos devueltos tras la solicitud de GraphQL

El parche de calidad MDVA-37288 para Adobe Commerce soluciona el problema de devolver precios de nivel incorrectos tras una solicitud de GraphQL. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23 está instalado. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

* El parche se ha diseñado para Adobe Commerce en la infraestructura en la nube 2.4.2
* El parche también es compatible con Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Añadir precios de nivel a cualquier artículo (por ejemplo, los precios de nivel se añadieron a artículos con id=1 e id=2).
1. Ejecute la consulta de GraphQL con una búsqueda que incluya los artículos con precios de nivel y los artículos sin precios de nivel.

<pre><code class="language-graphql">
{
  products(pageSize: 20, currentPage: 1, search: "24-MB0") {
    items {
      id
      price_tiers {
        quantity
        final_price {
          value
        }
      }
    }
  }
}
</code></pre>

<u>Resultados esperados</u>:

Solo los artículos con precios de nivel deben devolver precios de nivel adecuados:

```json
{
  "data": {
        "products": {
            "items": [
                {
                    "id": 17,
                    "price_tiers": []
                },
                {
                    "id": 1,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 23,
                    "price_tiers": []
                },
                {
                    "id": 19,
                    "price_tiers": []
                }
            ]
        }
    }
}
```

<u>Resultados reales</u>:

* Todos los artículos que siguen a un artículo con precios de nivel tienen precios de nivel en la respuesta.
* Los datos de precios de nivel que devuelve son del último elemento del bucle que tenía precios de nivel.

ejemplo de respuesta:

```json
{
    "data": {
        "products": {
            "items": [
                {
                    "id": 17,
                    "price_tiers": []
                },
                {
                    "id": 1,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 23,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                },
                {
                    "id": 19,
                    "price_tiers": [
                        {
                            "quantity": 1,
                            "final_price": {
                                "value": 34
                            }
                        },
                        {
                            "quantity": 5,
                            "final_price": {
                                "value": 32
                            }
                        }
                    ]
                }
            ]
        }
    }
}
```


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en nuestra documentación para desarrolladores, según el producto de Adobe Commerce:

* Adobe Commerce y Magento Open Source locales: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad en nuestra base de conocimiento de asistencia, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) en nuestra base de conocimiento de asistencia.
