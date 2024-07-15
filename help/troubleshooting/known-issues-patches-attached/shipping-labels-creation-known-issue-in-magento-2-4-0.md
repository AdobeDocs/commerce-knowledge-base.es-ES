---
title: Problema conocido de creación de etiquetas de envío en Adobe Commerce 2.4.0
description: Este artículo proporciona un parche para un problema conocido de Adobe Commerce 2.4.0, en el que no se puede crear una etiqueta de envío.
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Problema conocido de creación de etiquetas de envío en Adobe Commerce 2.4.0

Este artículo proporciona un parche para un problema conocido de Adobe Commerce 2.4.0, en el que no se puede crear una etiqueta de envío.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Requisitos previos</u>: cree un pedido con el método de envío FedEx, DHL, UPS o USPS.

### Escenario 1: crear una etiqueta al añadir un envío

<u>Pasos a seguir:</u>

1. Abra el pedido realizado en el Administrador, en **Ventas** > **Pedidos**.
1. Haga clic en el botón **Enviar**. Se abre la página **Nuevo envío**.

<u>Resultado esperado:</u>

La casilla **Crear etiqueta de envío** se muestra en la parte inferior de la página.

<u>Resultado real:</u>

No se muestra la casilla de verificación **Crear etiqueta de envío**.

### Escenario 2: crear una etiqueta para el envío existente

<u>Pasos a seguir:</u>

1. Abra el pedido realizado en el Administrador, en **Ventas** > **Pedidos**.
1. Haga clic en el botón **Enviar**. Se abre la página **Nuevo envío**.
1. Haz clic en el botón **Enviar envío**. Se crea un envío.
1. Abra el envío recién creado.
1. Haga clic en el botón **Crear etiqueta de envío**. Se abre el cuadro de diálogo **Crear paquetes**.

<u>Resultado esperado:</u>

El botón **Agregar productos al paquete** de la ventana modal **Crear paquetes** muestra campos con elementos de pedido.

<u>Resultado real:</u>

La ventana modal **Crear paquetes** no se muestra correctamente, no es posible agregar artículos de pedido al envío.

## Solución

Aplique el parche proporcionado en este artículo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[MC-35514-2.4.0-CE-composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

El parche también está disponible para su descarga en los formatos `.git` y `.composer` de la página [Descargas de Adobe Commerce](https://magento.com/tech-resources/download), en **Parches** en la navegación de la columna izquierda. Busque el parche de MC-35514.

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en la infraestructura en la nube versión 2.4.0
* Adobe Commerce local versión 2.4.0

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
