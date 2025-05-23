---
title: Pagos fallidos con tarjeta de crédito en un entorno de zona protegida
description: Este artículo explica por qué una tarjeta de crédito de prueba falla en un entorno de espacio aislado con API de PayPal.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 958067830d32b1f10ffa669307ec76d1e14b82a4
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Pagos fallidos con tarjeta de crédito en un entorno de zona protegida

Este artículo explica por qué una tarjeta de crédito de prueba falla en un entorno de espacio aislado con API de PayPal.

## Productos y versiones afectados

* Adobe Commerce 2.4.0 - 2.4.4 , todas las opciones de implementación, con [Servicios de pago](https://marketplace.magento.com/magento-payment-services.html)

## Problema

Cuando se usa una tarjeta de crédito Visa de prueba `4111 1111 1111 1111` de PayPal, a veces falla debido a las políticas de fraude de PayPal con el siguiente error:

```bash
Error happened when processing the request. Please try again later.
```

## Causa

Este error se muestra cuando PayPal marca un número de tarjeta de crédito de prueba específico para detectar fraudes. Esto sucede porque es un número de tarjeta de crédito de prueba utilizado por todos en el mundo para probar con las API de PayPal.

## Solución

Utilice otra tarjeta de crédito de prueba. Para generar tarjetas de crédito simuladas, puede utilizar para realizar pruebas:

1. Vaya a la página del PayPal Developer Portal [Generador de tarjetas de crédito](https://developer.paypal.com/api/rest/sandbox/card-testing/#link-creditcardgenerator).
1. Inicie sesión en el panel de PayPal Developer Portal.
1. Generar una tarjeta de crédito de prueba.
