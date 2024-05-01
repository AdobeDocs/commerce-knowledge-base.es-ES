---
title: "Problema conocido de Adobe Commerce 2.4.0: Páginas en blanco de mensajería en el sitio de Klarna"
description: En este artículo se describe un problema conocido de Adobe Commerce 2.4.0 con el método de pago Klarna, por el que, al habilitar la mensajería en el sitio de Klarna sin especificar un tema de diseño, no se muestran correctamente las páginas de productos en la tienda (las páginas de productos aparecen en blanco).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
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
1. Establecer **Activar** hasta *Sí*.
1. Deje el **Tema de diseño** en blanco.
1. Guarde la configuración haciendo clic en **Guardar configuración**.
1. Vaya a la tienda y navegue a cualquier página de producto.

<u>Resultado esperado:</u>

La página se carga correctamente con el tema de diseño predeterminado aplicado a la mensajería en el sitio de Klarna.

<u>Resultado real:</u>

Se muestra una página en blanco.

## Solución

Si habilita la mensajería en el sitio de Klarna, asegúrese siempre de que la variable **Tema de diseño** El campo no está en blanco.
