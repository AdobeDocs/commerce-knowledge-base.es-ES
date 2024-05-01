---
title: "Problema de Adobe Commerce 2.4.1: no se puede cambiar la cuenta de Amazon en Chrome"
description: En este artículo se describe un problema conocido de Adobe Commerce 2.4.1 en el que los clientes inician sesión en las cuentas de Amazon utilizadas anteriormente en lugar de sugerirles que inicien sesión al usar Amazon Pay durante el cierre de compra.
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Problema de Adobe Commerce 2.4.1: no se puede cambiar la cuenta de Amazon en Chrome

En este artículo se describe un problema conocido de Adobe Commerce 2.4.1 en el que los clientes inician sesión en las cuentas de Amazon utilizadas anteriormente en lugar de sugerirles que inicien sesión al usar Amazon Pay durante el cierre de compra.

## Productos y versiones afectados

* Adobe Commerce local 2.4.1
* Adobe Commerce en la infraestructura en la nube 2.4.1

## Problema

Los clientes inician sesión en las cuentas de Amazon usadas anteriormente en lugar de sugerirles que inicien sesión al usar Amazon Pay durante el cierre de compra.

<u>Pasos a seguir:</u>

1. En la tienda, agrega cualquier artículo al carro de compras y pasa al proceso de pago y envío de invitados.
1. Haga clic en **Amazon Pay** botón. Aparecerá la ventana emergente de inicio de sesión de Amazon.com.
1. Inicie sesión en la cuenta de Amazon.
1. Seleccione una dirección y haga clic en **Siguiente**.
1. Seleccione la forma de pago.
1. Clic **Realizar pedido**.
1. Vuelva a la página principal e inicie sesión en la cuenta de la tienda.
1. Vuelva a añadir cualquier artículo al carro de compras y continúe con el cierre de compra.
1. Haga clic en **Amazon Pay** botón.

<u>Resultado real:</u>

Vuelve a iniciar sesión automáticamente en la cuenta de Amazon utilizada anteriormente (Paso 3).

<u>Resultado esperado:</u>

Amazon.com aparece la ventana emergente de inicio de sesión, donde puedes iniciar sesión o crear una nueva cuenta para Amazon Pay.

## Causa

El problema puede producirse en una de las siguientes situaciones:

* Si la variable `SameSite` el valor de cookie es `LAX`, la cookie no se enviará como parte de ninguna llamada de terceros.
* La función de bloqueo de contenido de Mozilla Firefox evita que terceros rastreen las actividades de los usuarios del navegador al bloquear el uso de scripts y mecanismos de almacenamiento del lado del cliente. Firefox utiliza un proveedor externo, Disconnect.me para proporcionar una lista de sitios de seguimiento que se van a bloquear. Amazon Pay utiliza un iframe en un sitio web de terceros para devolver un token de acceso después de iniciar sesión y procesar la widget de dirección y billetera. Con la función de bloqueo de contenido, las solicitudes de carga de iframe de Amazon Pay se consideran solicitudes de seguimiento de terceros y se bloquean, lo que impide al comprador continuar con el cierre de compra.
* Cualquier situación en la que el explorador bloquee explícitamente las cookies de terceros o JS.

## Solución

Asegúrese de que los exploradores no bloqueen las solicitudes de iframe de Amazon Pay.
