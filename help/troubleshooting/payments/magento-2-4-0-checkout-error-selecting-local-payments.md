---
title: 'Adobe Commerce 2.4.0: error de cierre de compra al seleccionar pagos locales'
description: 'Este artículo trata sobre una solución para un problema conocido en Adobe Commerce durante el cierre de compra, donde aparece un mensaje de error al seleccionar un método de pago local para algunos países. Esto ocurre en los siguientes países: Bélgica, Italia, Países Bajos, Polonia y España.'
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%
---
# Adobe Commerce 2.4.0: error de cierre de compra al seleccionar pagos locales

Este artículo trata sobre una solución para un problema conocido en Adobe Commerce durante el cierre de compra, donde aparece un mensaje de error al seleccionar un método de pago local para algunos países. Esto ocurre en los siguientes países: Bélgica, Italia, Países Bajos, Polonia y España.

El mensaje de error &quot;*Actualmente no hay métodos de pago disponibles. Actualice la dirección de facturación.*&quot; aparecerán, pero los métodos de pago locales seguirán apareciendo y funcionando correctamente. Habrá disponible una corrección permanente en Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Requisitos previos</u>:

* Adobe Commerce 2.4.0 está instalado.
* Crear un producto y una categoría.
* Configurar [método de pago Braintree](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/).

<u>Pasos a seguir</u>:

1. Vaya a la tienda.
1. Seleccionar elementos para agregarlos al carro de compras.
1. Continúe con el cierre de compra.
1. Rellene el formulario de dirección con una dirección válida.
1. Acceda a la página Revisión y Pagos.

<u>Resultado esperado</u>:

Los métodos de pago locales deben mostrarse normalmente, sin mensaje de error.

<u>Resultado real</u>:

El mensaje de error &quot;*Actualmente no hay métodos de pago disponibles. Actualice la dirección de facturación.*&quot; aparece, pero los métodos de pago locales seguirán mostrándose y funcionando correctamente.

## Solución

La solución es ignorar el mensaje de error mostrado y continuar con el pago como de costumbre, ya que todos los métodos de pago locales funcionarán normalmente. La corrección estaba disponible a partir de la versión 2.4.1 de Adobe Commerce.

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
