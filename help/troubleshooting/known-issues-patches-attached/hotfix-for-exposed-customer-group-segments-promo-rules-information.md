---
title: Nombres de grupos de clientes, segmentos e información de reglas promocionales expuesta a través de  [!DNL GraphQL]
description: Este artículo proporciona una revisión para evitar la exposición de los nombres de grupos de clientes, segmentos de clientes e información de reglas promocionales a través de  [!DNL GraphQL].
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Nombres de grupos de clientes, segmentos e información de reglas promocionales expuestos a través de [!DNL GraphQL]

Este artículo proporciona una revisión para evitar la exposición de los nombres de grupos de clientes, segmentos de clientes e información de reglas promocionales a través de [!DNL GraphQL]. Está programado que el problema se corrija en Adobe Commerce 2.4.8-p1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

## Problema

Para [!UICONTROL Storefront Personalization Drop-ins], se introdujeron nuevas mutaciones [!DNL GraphQL] para mostrar información básica como nombres de grupos de clientes, segmentos, carrito y reglas de catálogo. Sin embargo, esto puede exponer datos confidenciales, como detalles de ofertas o códigos de cupones, si se incluyen en los nombres.

### Pasos a seguir

#### Caso I: [!UICONTROL Catalog Rule]

1. En la barra lateral *Admin*, vaya a **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Defina las condiciones de la regla (por ejemplo, atributo o categoría del producto).
1. Guarde y aplique la regla.
1. Asegúrese de que un producto cumpla las condiciones de la regla.
1. Ejecute la siguiente consulta [!DNL GraphQL] para recuperar todas las reglas:

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. Consulte un producto para comprobar si se aplica la regla:

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### Caso II: [!UICONTROL Cart Rule]

1. En la barra lateral *Admin*, vaya a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Establecer condiciones como valor mínimo del carro de compras y grupo de clientes.
1. Guarde y aplique la regla.
1. Añada productos al carro de compras para almacenar en déclencheur la regla.
1. Usar [!DNL GraphQL] para verificar todas las reglas del carro de compras:

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. Comprobar si se aplican reglas al carro de compras activo:

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### Caso III: [!UICONTROL Customer Group]

1. En la barra lateral *Admin*, vaya a **[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]**.
1. Compruebe que existen los grupos esperados.
1. Usar [!DNL GraphQL] para recuperar todos los grupos:

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. Verifique el grupo del cliente/invitado:

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### Caso IV: [!UICONTROL Customer Segment] (solo para Adobe Commerce)

1. En la barra lateral *Admin*, vaya a **[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]**.
1. Defina condiciones basadas en el cliente (por ejemplo, pedidos, contenido del carro de compras).
1. Asignar ámbito aplicable: *[!UICONTROL Visitor]*, *[!UICONTROL Registered]* o ambos.
1. Asegúrese de que las condiciones coincidan con un cliente de prueba.
1. Use [!DNL GraphQL] para comprobar todos los segmentos:

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. Validar los segmentos aplicados a un carro de compras:

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u>Resultado esperado</u>:

Los nombres de los grupos de clientes, los segmentos y la información de reglas promocionales no se exponen a través de [!DNL GraphQL].

<u>Resultado real</u>:

Los nombres de los grupos de clientes, los segmentos y la información de reglas promocionales se exponen a través de [!DNL GraphQL].

## Solución

Aplique los parches adjuntos según la versión de Adobe Commerce:

* Para la versión 2.4.8 de Adobe Commerce:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* Para [!DNL Magento], abra la versión 2.4.8 de Source:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
