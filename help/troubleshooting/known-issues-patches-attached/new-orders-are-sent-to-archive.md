---
title: Los nuevos pedidos se envían al archivo
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.0 relacionado con los pedidos recién creados que se muestran en el archivo en lugar de en la cuadrícula Pedidos del administrador de Commerce.
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Los nuevos pedidos se envían al archivo

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.0 relacionado con los pedidos recién creados que se muestran en el archivo en lugar de en la cuadrícula Pedidos del administrador de Commerce.

>[!NOTE]
>
>El problema se solucionó en 2.2.3 y versiones posteriores.

## Problema

Cuando los clientes realizan pedidos, aparecen en la cuadrícula de pedidos archivados en lugar de en la cuadrícula de pedidos normal.

<u>Pasos a seguir</u>:

1. Añada cualquier producto al carro de compras en la tienda, continúe con el cierre de compra y realice el pedido.
1. En el Administrador de Commerce, vaya a **Ventas** > **Operaciones** > **Pedido**. Ver el orden que aparece en la cuadrícula.
1. Vaya a **Ventas** > **Archivo** > **Pedidos**. Consulte el nuevo orden en la cuadrícula.

<u>Resultados esperados</u>:

El pedido solo se muestra en la cuadrícula Pedidos.

<u>Resultados reales</u>:

El orden se muestra en la cuadrícula Pedidos y en la cuadrícula del archivo de pedidos.

## Solución

Después de aplicar el parche, los pedidos aparecerán en la cuadrícula de pedidos según lo esperado. Sin embargo, debe restaurar manualmente en el administrador de Commerce los que se enviaron al archivo antes de aplicar el parche.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-8007\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce 2.2.0

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce local, Adobe Commerce en infraestructura en la nube 2.2.1 - 2.2.3

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Vínculos útiles en nuestra guía del usuario

* [Administrar pedidos archivados](https://docs.magento.com/user-guide/sales/order-archive.html)

## Archivos adjuntos
