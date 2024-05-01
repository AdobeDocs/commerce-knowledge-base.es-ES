---
title: Pago y envío se atasca cuando se utiliza el método de pago Authorize.net
description: Este artículo explica y corrige el problema de Adobe Commerce 2.3.X en el que la desprotección se atasca si se utiliza Authorize.net, con el mensaje de error *'No se puede leer la propiedad 'length' de null'* en el registro de la consola del explorador.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Pago y envío se atasca cuando se utiliza el método de pago Authorize.net

Este artículo explica y corrige el problema de Adobe Commerce 2.3.X, en el que el cierre de compra se atasca si se utiliza Authorize.net, con *&#39;No se puede leer la propiedad &#39;length&#39; de null&#39;* mensaje de error en el registro de la consola del explorador.

## Productos y versiones afectados

* Adobe Commerce 2.3.X

>[!NOTE]
>
>La integración de pagos principal de Adobe Commerce Authorize.Net ha quedado obsoleta desde la versión 2.3.4 y se eliminó completamente en la versión 2.4.0. Utilice una extensión que se adapte a sus necesidades desde el [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/) en su lugar.

## Problema

<u>Pasos a seguir</u>

1. Configure el método de pago Authorize.net en el Administrador de Commerce.
1. Ve a la tienda.
1. Añada un producto al carro de compras y continúe con el cierre de compra.
1. Elige Authorize.net como forma de pago.
1. Clic **Realizar pedido**.

<u>Resultado esperado</u>

Se carga el iframe de Authorize.net.

<u>Resultado real</u>

Se muestra el indicador de número de Ajax y la página nunca se carga. El siguiente error de JS se muestra en el registro de la consola del explorador: *&#39;TypeError no capturado: No se puede leer la propiedad &#39;length&#39; de null en b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;)*

## Causa

Una de las razones más comunes de este problema es que la clave de cliente pública no se especifica en la configuración de Authorize.Net en el administrador de Commerce.

## Solución

En **Tiendas** > **Configuración** > **Configuración** > **Ventas** > **Métodos de pago**, en el **Authorize.net** , compruebe si el valor se especifica en la sección **Clave de cliente pública** field. Si está vacío, introduzca el valor clave de su cuenta de comerciante Authorize.Net.

Para que se apliquen los cambios, limpie la caché ejecutando

```bash
bin/magento cache:clean
```
