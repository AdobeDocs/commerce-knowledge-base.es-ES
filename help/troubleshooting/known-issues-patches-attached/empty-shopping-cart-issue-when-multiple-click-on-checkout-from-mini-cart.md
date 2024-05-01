---
title: Problema con el carro de compras vacío cuando se hace clic en el cierre de compra del minicarrito
description: Este artículo proporciona un parche para un problema conocido de Adobe Commerce 2.2.3 relacionado con un carro de compras que está vacío después de que los clientes hagan clic varias veces en **Ir al cierre de compra** en el minicarrito de compras.
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Problema con el carro de compras vacío cuando se hace clic en el cierre de compra del minicarrito

Este artículo proporciona un parche para un problema conocido de Adobe Commerce 2.2.3 relacionado con un carro de compras vacío después de que los clientes hagan clic en **Ir a Cierre de compra** varias veces en el minicarrito de compras.

## Problema

Los clientes añaden productos al carro de compras e intentan cerrar la compra haciendo clic en **Ir a Cierre de compra** botón varias veces, pero cuando acceden al carro de compras, este está vacío. Es posible que el minicarrito siga mostrando productos.

<u>Pasos a seguir</u> :

1. Abra una página de producto en la tienda.
1. Añadir productos al carro de compras.
1. En el minicarrito de compras, haga clic en **Ir a Cierre de compra** varias veces.

<u>Resultado esperado</u> :

El carro de compras contiene todos los productos que ha agregado.

<u>Resultado real</u> :

No tiene elementos en el carro de compras.

## Parche

Los parches se adjuntan a este artículo. Para descargar un parche, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre de archivo necesario o haga clic en uno de los siguientes vínculos:

[Descargar MDVA-10441\_EE\_2.2.3\_v3.composer.patch](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[Descargar MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### Versiones de Adobe Commerce compatibles

Los parches se han creado para:

* Adobe Commerce local 2.2.3 (la `MDVA-10441_EE_2.2.3_v3.composer.patch` file)
* Adobe Commerce en la infraestructura en la nube 2.2.5 (`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` file)

El `MDVA-10441_EE_2.2.3_v3.composer.patch` Este parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en las versiones de infraestructura en la nube de 2.2.1 a 2.2.5
* Versiones locales de Adobe Commerce de 2.2.1 a 2.2.5

El `MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` Este parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce 2.2.5

## Cómo aplicar un parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Archivos adjuntos
