---
title: 'Adobe Commerce 2.4.0: excepción durante la instalación de B2B 1.2.0'
description: Este artículo proporciona una corrección de un problema conocido de Adobe Commerce por una excepción producida durante setup:upgrade al instalar B2B 1.2.0.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '317'
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

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones sobre el parche del compositor.

<u>parche de Git </u>

* Consulte [Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en la documentación para desarrolladores para obtener instrucciones sobre los parches de Git para Adobe Commerce en la infraestructura en la nube.
* Consulte [Aplicación de parches: parches personalizados](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) en la documentación para desarrolladores para obtener instrucciones sobre los parches de Git para Adobe Commerce.

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: los métodos de pago de Braintree no aparecen en el cierre de compra de varias direcciones](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema conocido de Adobe Commerce 2.4.0: mensaje de error al seleccionar el método de pago local que se muestra para algunos países durante el cierre de compra](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
