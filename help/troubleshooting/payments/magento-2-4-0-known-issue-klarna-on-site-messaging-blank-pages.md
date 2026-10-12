---
title: 'Problema conocido de Adobe Commerce 2.4.0: Páginas en blanco de mensajería en el sitio de Klarna'
description: En este artículo se describe un problema conocido de Adobe Commerce 2.4.0 con el método de pago Klarna, por el que, al habilitar la mensajería en el sitio de Klarna sin especificar un tema de diseño, no se muestran correctamente las páginas de productos en la tienda (las páginas de productos aparecen en blanco).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%
---
# Problema conocido de Adobe Commerce 2.4.0: Páginas en blanco de mensajería en el sitio de Klarna

En este artículo se describe un problema conocido de Adobe Commerce 2.4.0 con el método de pago Klarna, por el que, al habilitar la mensajería en el sitio de Klarna sin especificar un tema de diseño, no se muestran correctamente las páginas de productos en la tienda (las páginas de productos aparecen en blanco).

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

<u>Requisitos previos:</u> El método de pago Klarna está habilitado.

<u>Pasos a seguir:</u>

1. En Commerce Admin, vaya a **Tiendas** > **Configuración** > **Ventas** > **Métodos de pago** > **Klarna** > **Mensajería en el sitio de Klarna**.
1. Establecer **Enable** en *Yes*.
1. Deje el campo **Diseño del tema** en blanco.
1. Para guardar la configuración, haga clic en **Guardar configuración**.
1. Vaya a la tienda y navegue a cualquier página de producto.

<u>Resultado esperado:</u>

La página se carga correctamente con el tema de diseño predeterminado aplicado a la mensajería en el sitio de Klarna.

<u>Resultado real:</u>

Se muestra una página en blanco.

## Solución

Si habilita la mensajería en el sitio de Klarna, asegúrese siempre de que el campo **Tema de diseño** no esté en blanco.
