---
title: Las muestras de productos configurables no se muestran tachadas cuando no hay existencias
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.2 relacionado con que las muestras de productos configurables están agotadas y no se muestran como tachadas en la tienda.
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Las muestras de productos configurables no se muestran tachadas cuando no hay existencias

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.2 relacionado con que las muestras de productos configurables están agotadas y no se muestran como tachadas en la tienda.

## Problema

Cuando tiene un producto configurable y, para una combinación de opciones determinada, el producto simple relacionado no está disponible, la muestra sigue disponible y se puede seleccionar en la tienda.

<u>Pasos a seguir</u>:

1. En el administrador de Commerce, cree un producto configurable con opciones para dos atributos: color (rojo, negro) y tamaño (S, M, L).
1. Establezca la cantidad como &quot;1&quot; para cada producto simple correspondiente.
1. En la tienda, agregue rojo, M producto al carro y cierre de compra.
1. En el Administrador, procese el pedido para que la cantidad del artículo se actualice a &quot;0&quot;.
1. Asegúrese de que no se permiten pedidos no satisfechos.
1. En la tienda, vaya a la misma página de producto y seleccione las mismas opciones: rojo, M.

<u>Resultados esperados</u>:

La muestra roja, M tiene una barra oblicua roja y no se puede seleccionar.

<u>Resultados reales</u>:

Se puede seleccionar la muestra roja, M.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-8215\_EE\_2.2.2\_v1.composer.patch](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce (todos los métodos de implementación) 2.2.2

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.2.0-2.2.3

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
