---
title: "Adobe Commerce 2.4.2 B2B: el descuento sigue siendo el cambio del método de pago"
description: En este artículo se describe una incidencia conocida de Adobe Commerce 2.4.2 B2B en la que persiste un descuento por métodos de pago después de un cambio de método de pago al cerrar la compra. No hay ninguna resolución disponible en este momento.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '215'
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

1. Crear un carro **Regla de precio** que está vinculado a una forma de pago (Ejemplo: Los usuarios de PayPal obtienen un descuento del 20 %).
1. Crea un pedido y selecciona PayPal como forma de pago. Se aplica el descuento.
1. Se aprueba la OC.
1. Vaya a la página de pago para completar el pedido.
1. Selecciona otra forma de pago.

<u>Resultados reales</u> :

El descuento por la forma de pago permanece aplicado al total del pedido.  No se muestra ningún mensaje de error. El propietario de la tienda podrá ver cómo se ha producido comprobando el historial de pedidos.

<u>Resultados esperados</u> : el descuento por método de pago se elimina del total del pedido, según lo esperado.

## Solución

No hay ninguna resolución disponible en este momento.
