---
title: Pago y envío se atasca cuando se utiliza el método de pago Authorize.net
description: Este artículo explica y corrige el problema de Adobe Commerce 2.3.X en el que la desprotección se atasca si se utiliza Authorize.net, con el mensaje de error *'No se puede leer la propiedad 'length' de null'* en el registro de la consola del explorador.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
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
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%
---
# Pago y envío se atasca cuando se utiliza el método de pago Authorize.net

Este artículo explica y corrige el problema de Adobe Commerce 2.3.X en el que la desprotección se atasca si se utiliza Authorize.net, con el mensaje de error *&#39;No se puede leer la propiedad &#39;length&#39; de null&#39;* en el registro de la consola del explorador.

## Productos y versiones afectados

* Adobe Commerce 2.3.X

>[!NOTE]
>
>La integración de pagos principal de Adobe Commerce Authorize.Net ha quedado obsoleta desde la versión 2.3.4 y se eliminó completamente en la versión 2.4.0. En su lugar, usa una extensión que se adapte a tus necesidades de [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/).

## Problema

<u>Pasos a seguir</u>

1. Configure el método de pago Authorize.net en el Administrador de Commerce.
1. Ve a la tienda.
1. Añada un producto al carro de compras y continúe con el cierre de compra.
1. Elige Authorize.net como forma de pago.
1. Haga clic en **Realizar pedido**.

<u>Resultado esperado</u>

Se carga el iframe de Authorize.net.

<u>Resultado real</u>

Se muestra el indicador de número de Ajax y la página nunca se carga. El siguiente error de JS se muestra en el registro de la consola del explorador: *&#39;TypeError no capturado: No se puede leer la propiedad &#39;length&#39; de null en b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*

## Causa

Una de las razones más comunes de este problema es que la clave de cliente pública no se especifica en la configuración de Authorize.Net en el administrador de Commerce.

## Solución

En **Tiendas** > **Configuración** > **Configuración** > **Ventas** > **Métodos de pago**, en la sección **Autorizar.net**, compruebe si el valor se especifica en el campo **Clave de cliente pública**. Si está vacío, introduzca el valor clave de su cuenta de comerciante Authorize.Net.

Para que se apliquen los cambios, limpie la caché ejecutando

```bash
bin/magento cache:clean
```
