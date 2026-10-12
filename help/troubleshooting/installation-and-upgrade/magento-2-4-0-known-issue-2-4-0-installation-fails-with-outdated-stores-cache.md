---
title: La instalación de Adobe Commerce 2.4.0 falla con la memoria caché de tiendas obsoletas
description: 'Este artículo proporciona una solución para el problema en el que la instalación de Adobe Commerce 2.4.0 falla con el siguiente mensaje de error: * El sitio web predeterminado no está definido. Configure el sitio web e inténtelo de nuevo.* se muestra en la consola.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%
---
# La instalación de Adobe Commerce 2.4.0 falla con la memoria caché de tiendas obsoletas

Este artículo proporciona una solución para el problema en el que la instalación de Adobe Commerce 2.4.0 falla con el siguiente mensaje de error: *El sitio web predeterminado no está definido. Establezca el sitio web y vuelva a intentarlo.* se muestra en la consola.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.0
* Adobe Commerce local 2.4.0

## Problema

<u>Requisitos previos:</u>
Una extensión de terceros con dependencias de API para el módulo Almacenar en comandos CLI se configura según se requiere en `composer.json`. Esto provoca que la instalación de Adobe Commerce 2.4.0 falle con un mensaje de error: *El sitio web predeterminado no está definido. Establezca el sitio web y vuelva a intentarlo.* se muestra en la consola.

## Causa

El problema aparece para las extensiones de terceros que dependen de almacenes en sus comandos CLI. Una es los Canales de ventas de Amazon.

## Solución

Antes de la instalación de Adobe Commerce 2.4.0, los comerciantes deben:

1. Quite estas extensiones de terceros de `composer.json`.
1. Instalar Adobe Commerce sin extensiones.
1. Añada las extensiones después de la instalación.

Este problema se solucionará en la versión 2.4.1 de.

## Lecturas relacionadas en nuestra base de conocimiento de soporte:

* [Problema conocido de Adobe Commerce 2.4.0: falta la etiqueta &quot;Reembolso&quot; en Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0, 2.4.1: Habilitar emisión de factura parcial de Braintree Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema conocido de Adobe Commerce 2.4.0: Amazon Pay habilitado, faltan métodos de pago al volver al cierre de compra estándar utilizado](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

