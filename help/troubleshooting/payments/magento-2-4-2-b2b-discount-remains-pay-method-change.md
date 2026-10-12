---
title: 'Adobe Commerce 2.4.2 B2B: el descuento sigue siendo el cambio del método de pago'
description: En este artículo se describe una incidencia conocida de Adobe Commerce 2.4.2 B2B en la que persiste un descuento por métodos de pago después de un cambio de método de pago al cerrar la compra. No hay ninguna resolución disponible en este momento.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%
---
# Adobe Commerce 2.4.2 B2B: el descuento sigue siendo el cambio del método de pago

En este artículo se describe una incidencia conocida de Adobe Commerce 2.4.2 B2B en la que persiste un descuento por métodos de pago después de un cambio de método de pago al cerrar la compra. No hay ninguna resolución disponible en este momento.

## Productos y versiones afectados

* Adobe Commerce 2.4.2
* Adobe Commerce en infraestructura en la nube 2.4.2
* B2B para Adobe Commerce 1.3.1


## Problema

<u>Pasos a seguir</u> :

1. Crea una **Regla de precio** del carro de compras que esté vinculada a un método de pago (Ejemplo: Los usuarios de PayPal obtienen un descuento del 20%).
1. Crea un pedido y selecciona PayPal como forma de pago. Se aplica el descuento.
1. Se aprueba la OC.
1. Vaya a la página de pago para completar el pedido.
1. Selecciona otra forma de pago.

<u>Resultados reales</u> :

El descuento por la forma de pago permanece aplicado al total del pedido.  No se muestra ningún mensaje de error.El propietario de la tienda podrá ver que esto ha sucedido comprobando el historial de pedidos.

<u>Resultados esperados</u> El descuento de método de pago :The se ha eliminado del total del pedido, tal como se esperaba.

## Solución

No hay ninguna resolución disponible en este momento.
