---
title: 'Problema conocido de Adobe Commerce 2.4.0: Amazon pay, sin métodos de pago'
description: Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 en el que faltan métodos de pago cuando los clientes utilizan **Volver al cierre de compra estándar**, después de habilitar Amazon Pay.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
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
source-wordcount: '201'
ht-degree: 0%
---
# Problema conocido de Adobe Commerce 2.4.0: Amazon pay, sin métodos de pago

Este artículo proporciona una solución para un problema conocido de Adobe Commerce 2.4.0 en el que faltan métodos de pago cuando los clientes usan **Volver al cierre de compra estándar**, una vez que han habilitado Amazon Pay.

## Productos y versiones afectados

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube v2.3.5.p1 y v2.4.0

<u>Pasos a seguir:</u>

1. Vaya a la tienda.
1. Añada cualquier elemento al carro de compras y continúe con el cierre de compra.
1. Inicie sesión en su cuenta de Amazon Pay.
1. Seleccione una dirección y continúe con el cierre de compra.
1. Haga clic en **Volver al cierre de compra estándar**.
1. Continúe con el cierre de compra.

<u>Resultados esperados:</u>

Los métodos de pago deben mostrarse después de reiniciar el cierre de compra.

<u>Resultados reales:</u>

Faltan métodos de pago.

## Solución

Se prevé una resolución para 2.4.1.

## Lecturas relacionadas en nuestra base de conocimiento de soporte:

* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
