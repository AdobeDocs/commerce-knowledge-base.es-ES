---
title: Los clientes cierran la sesión o pierden contenido del carro de compras en la tienda Adobe Commerce
description: Este artículo proporciona una solución y solución al problema de que los clientes cierren la sesión o pierdan elementos del carro de compras en la tienda después de que se les redirija de nuevo a la tienda Adobe Commerce desde el pago u otros servicios de terceros (la cookie de sesión se "pierde").
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Los clientes cierran la sesión o pierden contenido del carro de compras en la tienda Adobe Commerce

Este artículo proporciona una solución al problema de que los clientes cierren la sesión o pierdan elementos del carro de compras en la tienda después de que se les redirija de nuevo a la tienda Adobe Commerce desde el pago u otros servicios de terceros (la cookie de sesión se &quot;pierde&quot;).

## Productos y versiones afectados

* Adobe Commerce local, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

<u>Pasos a seguir:</u>

1. El cliente agrega productos al carro de compras en la tienda y continúa con el cierre de compra.
1. Se redirige al cliente al sitio de terceros para realizar el pago o el envío, así como para obtener otra información o servicio.
1. Se redirige al cliente a la tienda.

<u>Resultado real:</u>

El cliente ha sido redirigido al carro de compras vacío o a una página en blanco.

<u>Resultado esperado:</u>

El cliente se redirige a una página de pago correcta (u otra página correcta), sin perder los datos de cierre de compra ni el progreso.

## Causa

El atributo de cookie SameSite se establece en *Laxo* o no especificado (que se trata como configurado en *Laxo* ). Tener `SameSite` = *Laxo* deshabilita la transferencia de una cookie a direcciones URL externas mediante `POST` solicitudes.

## Solución

Para resolver el problema, póngase en contacto con el proveedor de servicios de terceros y solicite a sus desarrolladores que actualicen sus integraciones para configurar los parámetros de las cookies.

## Lectura relacionada

[Actualización de SameSite de Chrome](https://www.chromestatus.com/feature/5088147346030592)
