---
title: Página de terminal virtual del Braintree de Adobe Commerce 2.4.0 dañada
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.4.0, en el que la página Terminal virtual del Braintree no carga los elementos de la interfaz de usuario adecuados o un mensaje de error adecuado si el Braintree no está configurado.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Página de terminal virtual del Braintree de Adobe Commerce 2.4.0 dañada

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.4.0, en el que la página Terminal virtual del Braintree no carga los elementos de la interfaz de usuario adecuados o un mensaje de error adecuado si el Braintree no está configurado.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

### Escenario 1: se ha configurado el método de pago del Braintree

<u>Pasos a seguir:</u>

En Commerce Admin, vaya a **Ventas** > **Terminal virtual de Braintree** . ** **

<u>Resultado esperado:</u>

El **Terminal virtual de Braintree** La página se carga con la IU adecuada.

<u>Resultado real:</u>

La interfaz de usuario de **Terminal virtual de Braintree** La página está rota.

### Escenario 2: se ha configurado el método de pago del Braintree

<u>Pasos a seguir:</u>

En Commerce Admin, vaya a **Ventas** > **Terminal virtual de Braintree** . ** **

<u>Resultado esperado:</u>

El **Terminal virtual de Braintree** La página se carga con la interfaz de usuario adecuada y se muestra una advertencia que indica que el Braintree aún no está configurado.

<u>Resultado real:</u>

La interfaz de usuario de **Terminal virtual de Braintree** La página está rota y no se muestra ninguna advertencia.

## Solución

Aplique el parche proporcionado en este artículo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en infraestructura en la nube 2.4.0
* Adobe Commerce local 2.4.0

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
