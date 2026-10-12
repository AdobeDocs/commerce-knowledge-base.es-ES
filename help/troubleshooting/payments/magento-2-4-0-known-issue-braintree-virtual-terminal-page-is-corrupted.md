---
title: Página de terminal virtual de Adobe Commerce 2.4.0 Braintree dañada
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.4.0, en el que la página Terminal virtual de Braintree no carga los elementos de la interfaz de usuario adecuados o un mensaje de error adecuado si Braintree no está configurado.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
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
source-wordcount: '304'
ht-degree: 0%
---
# Página de terminal virtual de Adobe Commerce 2.4.0 Braintree dañada

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.4.0, en el que la página Terminal virtual de Braintree no carga los elementos de la interfaz de usuario adecuados o un mensaje de error adecuado si Braintree no está configurado.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

### Escenario 1: se ha configurado el método de pago Braintree

<u>Pasos a seguir:</u>

En Commerce Admin, vaya a **Ventas** > **Terminal virtual de Braintree** . ** **

<u>Resultado esperado:</u>

La página **Terminal virtual de Braintree** se carga con la interfaz de usuario adecuada.

<u>Resultado real:</u>

La interfaz de usuario de la página **Terminal virtual de Braintree** está dañada.

### Escenario 2: se ha configurado el método de pago Braintree

<u>Pasos a seguir:</u>

En Commerce Admin, vaya a **Ventas** > **Terminal virtual de Braintree** . ** **

<u>Resultado esperado:</u>

La página **Terminal virtual de Braintree** se carga con la interfaz de usuario adecuada y se muestra una advertencia que indica que Braintree aún no se ha configurado.

<u>Resultado real:</u>

La interfaz de usuario de la página **Terminal virtual de Braintree** está dañada y no se muestra ninguna advertencia.

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

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) para obtener instrucciones.

## Archivos adjuntos
