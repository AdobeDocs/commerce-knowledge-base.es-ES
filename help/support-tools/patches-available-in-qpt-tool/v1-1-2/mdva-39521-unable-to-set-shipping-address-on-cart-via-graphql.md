---
title: "MDVA-39521: No se puede establecer la dirección de envío en los carros de compras mediante GraphQL"
description: El parche MDVA-39521 resuelve el problema en el que el usuario no puede establecer la dirección de envío en carros con un número de teléfono vacío a través de GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-39521. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: b6bb4e83-ba65-4f15-82be-1252d9beb2fb
feature: GraphQL, Orders, Shipping/Delivery, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# MDVA-39521: no se puede establecer la dirección de envío en los carros de compras mediante GraphQL

El parche MDVA-39521 resuelve el problema en el que el usuario no puede establecer la dirección de envío en carros con un número de teléfono vacío a través de GraphQL. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-39521. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario no puede establecer la dirección de envío en los carros con un número de teléfono vacío a través de GraphQL a pesar de que Mostrar teléfono está configurado como opcional.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Vaya a **Tiendas** > **Configuración** > **Clientes** > **Configuración del cliente** > **Opciones de nombre y dirección** y establezca Mostrar teléfono como opcional.
1. Cree un carro vacío mediante una solicitud de GraphQL.

   ```GraphQL
   mutation {
   createEmptyCart
   }
   ```

1. Añadir producto al carro de compras.

   ```GraphQL
   mutation {
   addSimpleProductsToCart(
   input: {
     cart_id: "{ CART_ID }"
     cart_items: [
       {
         data: {
           quantity: 1
           sku: "24-MG04"
         }
       }
     ]
   }
   ) {
   cart {
     items {
       id
       product {
         sku
         stock_status
       }
       quantity
     }
   }
   }
   }
   ```

1. Añadir dirección: GRAPHQL VARIABLES.

   ```GraphQL
   {
     "cartId": "6Efw00UbjPoP5cvTFhsswDTjpxs0Xupt"
   }
   ```

   ```GraphQL
   mutation ($cartId: String!) {
     setShippingAddressesOnCart(input: {cart_id: $cartId, shipping_addresses:
     {address: {firstname: "John", lastname: "Doe", company: "Company Name",
     street: ["820 Burrard Street"], city: "Vancouver", region: "BC", postcode: "V6Z 2J1",
     country_code: "CA", telephone: "123-456-0000", save_in_address_book: false}}}) {
       cart {
         shipping_addresses {
           firstname
           lastname
           company
           street
           city
           postcode
           telephone
           country {
             code
             label
           }
         }
       }
     }
   }
   ```

   Resultado:

   ```GraphQL
     {
         "data": {
             "setShippingAddressesOnCart": {
                 "cart": {
                     "shipping_addresses": [
                         {
                             "firstname": "John",
                             "lastname": "Canada",
                             "company": "Company Name",
                             "street": [
                                 "820 Burrard Street"
                             ],
                             "city": "Vancouver",
                             "postcode": "V6Z 2J1",
                             "telephone": "123-456-0000",
                             "country": {
                                 "code": "CA",
                                 "label": "CA"
                             }
                         }
                     ]
                 }
             }
         }
     }
   ```

1. Añada una dirección con un número de teléfono vacío.

   ```GraphQL
   mutation ($cartId: String!) {
     setShippingAddressesOnCart(input: {cart_id: $cartId, shipping_addresses: {address: {firstname:
       "John", lastname: "Canada", company: "Company Name", street: ["820 Burrard Street"], city:
       "Vancouver", region: "BC", postcode: "V6Z 2J1", country_code: "CA", telephone: "123-456-0000",
       save_in_address_book: false}}}) {
       cart {
         shipping_addresses {
           firstname
           lastname
           company
           street
           city
           postcode
           telephone
           country {
             code
             label
           }
         }
       }
     }
   }
   ```

<u>Resultados esperados</u>:

```GraphQL
 {
    "data": {
        "setShippingAddressesOnCart": {
            "cart": {
                "shipping_addresses": [
                    {
                        "firstname": "John",
                        "lastname": "Doe",
                        "company": "Company Name",
                        "street": [
                            "820 Burrard Street"
                        ],
                        "city": "Vancouver",
                        "postcode": "V6Z 2J1",
                        "telephone": "",
                        "country": {
                            "code": "CA",
                            "label": "CA"
                        }
                    }
                ]
            }
        }
    }
 }
```

<u>Resultados reales</u>:

```GraphQL
{
    "data": {
        "setShippingAddressesOnCart": {
            "cart": {
                "shipping_addresses": []
            }
        }
    }
}
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
