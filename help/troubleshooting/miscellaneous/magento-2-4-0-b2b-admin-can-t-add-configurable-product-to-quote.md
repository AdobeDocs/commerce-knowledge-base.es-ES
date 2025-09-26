---
title: El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto
description: Este artículo trata sobre un problema conocido en Commerce Admin al administrar una cotización B2B; no es posible añadir un producto configurable por **SKU** a la cotización. Al hacer clic en el botón **Añadir a cotización**, la página de edición **Oferta** se queda atascada al cargarse y no puede configurar el producto y guardar los cambios. Este problema también se produce en Administración al añadir un producto por **SKU** a un pedido o al añadir un producto por **SKU** en **Cierre de compra avanzado** (**Administración** &gt; **Clientes** &gt; **Todos los clientes** &gt; **Edición del cliente** &gt; **Gestionar el carro de compras**). Este problema se resolverá en un parche para Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto

Este artículo trata sobre un problema conocido en Commerce Admin al administrar una cotización B2B. No es posible agregar un producto configurable por **SKU** a la cotización. Al hacer clic en el botón **Agregar al presupuesto**, la página de edición de **Presupuesto** se atasca al cargarse y no puede configurar el producto y guardar los cambios. Este problema también se produce en Administración al agregar un producto por **SKU** a un pedido o al agregar un producto por **SKU** en **Cierre de compra avanzado** (**Administrador** > **Clientes** > **Todos los clientes** > **Edición del cliente** > **Administrar el carro de compras**). Este problema se resolverá en un parche para Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Condiciones previas</u>

* Adobe Commerce 2.4.0 está instalado.
* B2B está instalado.
* Definir características B2B en **Habilitar compañía =** *Sí* , **Habilitar catálogo compartido =** *No* y **Habilitar cotización B2B =** *Sí*.
* Cree una cuenta de cliente.
* Cree una cuenta de compañía con el cliente creado anteriormente como administrador de la compañía.
* Cree un producto simple (Ejemplo: name &amp; **SKU** = TEST SIMPLE 1) que no esté asignado a **Predeterminado (General)**.
* Pida al administrador de la empresa que solicite una cotización utilizando el producto simple creado anteriormente (Ejemplo: TEST SIMPLE 1).

<u>Pasos a seguir</u>

1. Vaya al panel de administración de Commerce.
1. Vaya a **Ventas > Ofertas**.
1. Abra **Cita**.
1. Haz clic en el botón **Agregar producto por SKU**.
1. Escriba el **SKU** de otro producto (ejemplo: TEST SIMPLE 2) en el campo de entrada **Introducir SKU**.
1. Escriba una cantidad válida en el campo de entrada **Cantidad**.
1. Haga clic en el botón **Agregar al presupuesto**.

<u>Resultados esperados</u>

* La cuadrícula **Productos no agregados al presupuesto**, que contiene el nombre y **SKU** del producto creado, aparece según lo esperado.
* Una vez configurado el producto, el administrador puede agregarlo al **Presupuesto** haciendo clic en el botón **Agregar productos al presupuesto**, según lo esperado.

<u>Resultados reales</u>

* No aparece la cuadrícula **Productos no agregados al presupuesto**, que contiene el nombre y **SKU** del producto creado.
* La página **Quote** está atascada cargándose.

## Recomendación

Actualmente, no hay solución para este problema con la edición de presupuestos B2B, pero para la administración de pedidos y carros de compras, es posible seleccionar productos de la **lista de productos** en lugar de agregarlos por **SKU**. Habrá disponible un parche para resolver el problema para Adobe Commerce 2.4.1, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: la actualización de las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)

