---
title: 'Mensaje de validación de dirección de vértice de Adobe Commerce 2.4.1: Actualización de dirección de publicación'
description: Este artículo describe un problema conocido de Adobe Commerce 2.4.1 en el que la validación de direcciones de Vértice no funciona durante la fase de pago cuando se utiliza una dirección de envío diferente a la de facturación. Se ha programado la corrección del problema en Adobe Commerce 2.4.2.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Mensaje de validación de dirección de vértice de Adobe Commerce 2.4.1: Actualización de dirección de publicación

Este artículo describe un problema conocido de Adobe Commerce 2.4.1 en el que la validación de direcciones de Vértice no funciona durante la fase de pago cuando se utiliza una dirección de envío diferente a la de facturación. Se ha programado la corrección del problema en Adobe Commerce 2.4.2.

## Productos y versiones afectados

* Adobe Commerce local 2.4.1 con la integración de Vertex habilitada
* Adobe Commerce en la infraestructura en la nube 2.4.1 con la integración de Vertex habilitada

## Problema

Requisitos previos:

Activar **Limpieza de direcciones de vértice**. Para ver los pasos, consulte [Configurar la limpieza de direcciones de tienda](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html) en nuestra guía del usuario.

<u>Pasos a seguir:</u>

1. Cree una cuenta e inicie sesión.
1. Añadir un elemento al carro de compras haciendo clic en **Añadir al carro**. Haga clic en el icono Carro de compras y luego en **Continuar con el cierre**.
1. Introduzca una dirección válida en **Dirección de envío** field.
1. Marque una de las opciones en **Métodos de envío**. Luego haga clic en **Siguiente**.
1. Si la validación de direcciones sugiere información de dirección diferente, haga clic en **Actualizar dirección** y haga clic en **Siguiente**.
1. Desmarque la **Mi dirección de facturación y envío es la misma** casilla de verificación

<u>Primer escenario:</u>

Siga las [más de seis pasos](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) y luego:

1. Introduzca una nueva dirección de facturación válida.
1. Haga clic en **Actualizar** botón. Mostrará el mensaje o la sugerencia de la siguiente manera: *La dirección no es válida.* A continuación se incluye una sugerencia de dirección como: *Código postal : XXXXX- XXXX Street : XXX City street XXX*
1. Haga clic en **Actualizar** botón (no haga clic en el **Actualizar dirección** botón de sugerencia de dirección de Vértice).
1. Haga clic en **Editar** de la dirección de facturación actualizada.
1. Seleccione la dirección de la lista desplegable de direcciones.
1. Haga clic en **Actualizar** botón.

<u>Resultado esperado:</u>

Se elimina el mensaje de validación o sugerencia antiguo.

<u>Resultado real:</u>

El mensaje/sugerencia de validación. *&quot;No hemos encontrado una dirección válida Código postal: XXXXX-XXXX Street : XXX City street XXX&quot;* el mensaje es **NO** eliminado. El mismo problema se produce si se introduce una dirección no válida en el formulario.

<u>Segundo escenario:</u>

Siga las [más de seis pasos](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) y luego:

1. Rellene el formulario de direcciones con una dirección válida.
1. Haga clic en **Actualizar** botón. Mostrará el mensaje o la sugerencia de la siguiente manera: *La dirección no es válida.* A continuación se incluye una sugerencia de dirección como: *Código postal : XXXXX-XXXX Street : XXX City street XXX*.
1. Haga clic en **Actualizar** botón (no haga clic en el **Actualizar dirección** botón de sugerencia de dirección de vértice).
1. Compruebe la ***Mi dirección de facturación y envío es la misma*** menú desplegable.

<u>Resultado esperado:</u>

Se elimina el mensaje de validación o sugerencia antiguo.

<u>Resultado real:</u>

El mensaje/sugerencia de validación. *&quot;No hemos encontrado una dirección válida Código postal: XXXXX-XXXX Street XXX City street XXX&quot;* el mensaje es **NO** eliminado. El mismo problema se produce si se introduce una dirección no válida en el formulario.

## Lectura relacionada en nuestra base de conocimiento de soporte:

[Problema conocido de Adobe Commerce 2.3.6, 2.4.0-p1 y 2.4.1: no se puede iniciar sesión en dotdigital cuando la cuenta está habilitada](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
