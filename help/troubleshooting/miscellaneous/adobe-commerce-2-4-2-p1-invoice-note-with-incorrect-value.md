---
title: 'Adobe Commerce 2.4.2-p1: nota de factura con un valor incorrecto'
description: Este artículo describe un problema conocido de Adobe Commerce 2.4.2-p1 en el que se genera una nota de factura con un valor incorrecto cuando se cambia el grupo de clientes al crear el pedido. Este problema se ha corregido en la versión 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '229'
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
1. En la sección **Información de la cuenta**, cambie el grupo de clientes de **Retailer** a **Gobierno**.
1. Haga clic en **Realizar pedido**.
1. Haga clic en **Factura** > **Enviar factura**.

<u>Resultados esperados</u>:

La nota siguiente debería aparecer en la sección **Notas de este pedido**: &quot;Factura de vértice enviada correctamente. Importe: 0,00 $&quot;.

<u>Resultados reales</u>:

La nota siguiente aparece en la sección **Notas de este pedido**: &quot;Factura de vértice enviada correctamente. Importe: 3,23 $&quot;.

## Solución

Este problema se ha corregido en la versión 2.4.3.
