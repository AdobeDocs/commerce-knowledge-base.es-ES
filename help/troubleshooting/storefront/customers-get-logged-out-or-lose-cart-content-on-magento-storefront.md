---
title: Los clientes cierran la sesión o pierden contenido del carro de compras en la tienda Adobe Commerce
description: Este artículo proporciona una solución y solución al problema de que los clientes cierren la sesión o pierdan elementos del carro de compras en la tienda después de que se les redirija de nuevo a la tienda Adobe Commerce desde el pago u otros servicios de terceros (la cookie de sesión se "pierde").
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '285'
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

El atributo de cookie SameSite se ha establecido en *Lax* o no se ha especificado (que se trata como establecido en *Lax* ). Tener `SameSite` = *Lax* deshabilita la transferencia de una cookie a direcciones URL externas a través de `POST` solicitudes.

## Solución

Para resolver el problema, póngase en contacto con el proveedor de servicios de terceros y solicite a sus desarrolladores que actualicen sus integraciones para configurar los parámetros de las cookies.

## Lectura relacionada

[Actualización de Chrome SameSite](https://www.chromestatus.com/feature/5088147346030592)
