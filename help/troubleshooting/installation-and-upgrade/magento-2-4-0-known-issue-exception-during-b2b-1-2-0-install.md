---
title: 'Adobe Commerce 2.4.0: excepción durante la instalación de B2B 1.2.0'
description: Este artículo proporciona una corrección de un problema conocido de Adobe Commerce por una excepción producida durante setup:upgrade al instalar B2B 1.2.0.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
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
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%
---
# Adobe Commerce 2.4.0: excepción durante la instalación de B2B 1.2.0

Este artículo proporciona una corrección de un problema conocido de Adobe Commerce para una excepción producida durante `setup:upgrade` al instalar B2B 1.2.0.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0
* B2B 1.2.0

## Problema

<u>Pasos a seguir</u>

1. Instale Adobe Commerce con más de una tienda creada.
1. Crear un almacén adicional.
1. Instale B2B 1.2.0.

>[!WARNING]
>
>La actualización de cualquier instancia B2B con más de un almacén desde una versión inferior a 1.2.0 o una instancia de Commerce inferior a 2.4.0 también se ve afectada.

<u>Resultado esperado</u>

Instalaciones de B2B 1.2.0.

<u>Resultado real</u>

Cuando `setup:upgrade` se ejecuta para instalar B2B 1.2.0, este error aparece en el módulo `PurchaseOrder`:

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## Solución

Aplique el parche proporcionado en este artículo.

## Parche

La revisión se adjunta a este artículo, disponible para su descarga en los formatos `.composer` y `.git` (después de descomprimir los archivos).

Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en uno de los siguientes vínculos:

* [parche del Compositor B2B-716\_composer.patch](assets/B2B-716_composer.patch.zip)
* [parche de Git B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## Cómo aplicar un parche

<u>Parche del compositor </u>

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) para obtener instrucciones sobre el parche del compositor.

<u>parche de Git </u>

* Consulte [Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en la documentación para desarrolladores para obtener instrucciones sobre los parches de Git para Adobe Commerce en la infraestructura en la nube.
* Consulte [Aplicación de parches: parches personalizados](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) en la documentación para desarrolladores para obtener instrucciones sobre los parches de Git para Adobe Commerce.

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
