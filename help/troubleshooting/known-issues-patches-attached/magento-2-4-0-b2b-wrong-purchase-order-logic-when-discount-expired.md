---
title: "Adobe Commerce 2.4.0 B2B: lógica de pedido de compra incorrecta cuando caducó el descuento"
description: Este artículo proporciona un parche para el problema conocido de que no se aplica un descuento en un pedido de compra en Adobe Commerce 2.4.0 B2B. Si el pedido se ha realizado con un código de descuento que ha caducado mientras el pedido estaba en proceso de aprobación, el pedido aprobado no refleja el descuento.
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B: lógica de pedido de compra incorrecta cuando caducó el descuento

Este artículo proporciona un parche para el problema conocido de que no se aplica un descuento en un pedido de compra en Adobe Commerce 2.4.0 B2B. Si el pedido se ha realizado con un código de descuento que ha caducado mientras el pedido estaba en proceso de aprobación, el pedido aprobado no refleja el descuento.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.0
* Adobe Commerce local 2.4.0

## Problema

<u>Requisitos previos</u>: se crea un cupón de descuento y existen automáticamente reglas de aprobación que impiden que se procesen las OC.

<u>Pasos a seguir:</u>

1. Realice un pedido con un descuento aplicado.
1. Desactive el cupón de descuento.
1. Aprobar PC como responsable.
1. Compruebe el pedido creado como resultado.

<u>Resultado esperado:</u>

El pedido se crea con un total descontado.

<u>Resultado real:</u>

El pedido se crea por el importe completo.

## Solución

Aplique el parche proporcionado en este artículo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

El parche también está disponible para su descarga en ambos, `.git` y `.composer` , formatos en [Descargas de Adobe Commerce](https://magento.com/tech-resources/download) página, debajo de **Parches** en la navegación de la columna izquierda. Busque el parche XXX.

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de asistencia para obtener instrucciones.
