---
title: "Adobe Commerce 2.4.2-p1: nota de factura con un valor incorrecto"
description: Este artículo describe un problema conocido de Adobe Commerce 2.4.2-p1 en el que se genera una nota de factura con un valor incorrecto cuando se cambia el grupo de clientes al crear el pedido. Este problema se ha corregido en la versión 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Adobe Commerce 2.4.2-p1: nota de factura con un valor incorrecto

Este artículo describe un problema conocido de Adobe Commerce 2.4.2-p1 en el que se genera una nota de factura con un valor incorrecto cuando se cambia el grupo de clientes al crear el pedido. Este problema se ha corregido en la versión 2.4.3.

## Productos y versiones afectados

* Adobe Commerce local 2.4.2-p1
* Adobe Commerce en infraestructura en la nube 2.4.2-p1

## Problema

Cuando se cambia el grupo de clientes en el momento de crear el pedido, la factura se genera con una nota de factura incorrecta.

<u>Pasos a seguir</u>:

1. Crear una **cuenta de cliente de prueba** y agregarla al **grupo de clientes minoristas**.
1. Cree un **nuevo pedido** para el cliente de prueba, agregue **producto** y **dirección**.
1. Seleccione **Método de envío**.
1. En la sección **Información de la cuenta**, cambie el grupo de clientes de **Minorista** a **Gobierno**.
1. Haga clic en **Realizar pedido**.
1. Haga clic en **Factura** > **Enviar factura**.

<u>Resultados esperados</u>:

La nota siguiente debería aparecer en la sección **Notas de este pedido**: &quot;Factura de vértice enviada correctamente. Importe: 0,00 $&quot;.

<u>Resultados reales</u>:

La nota siguiente aparece en la sección **Notas de este pedido**: &quot;Factura de vértice enviada correctamente. Importe: 3,23 $&quot;.

## Solución

Este problema se ha corregido en la versión 2.4.3.
