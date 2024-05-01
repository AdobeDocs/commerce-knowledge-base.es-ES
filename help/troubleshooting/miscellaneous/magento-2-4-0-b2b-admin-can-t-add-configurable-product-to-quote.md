---
title: El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto
description: Este artículo trata sobre un problema conocido en Commerce Admin al administrar una cotización B2B; no es posible añadir un producto configurable por **SKU** a la cotización. Al hacer clic en el botón **Añadir a cotización**, la página de edición **Oferta** se queda atascada al cargarse y no puede configurar el producto y guardar los cambios. Este problema también se produce en Administración al añadir un producto por **SKU** a un pedido o al añadir un producto por **SKU** en **Cierre de compra avanzado** (**Administración** &gt; **Clientes** &gt; **Todos los clientes** &gt; **Edición del cliente** &gt; **Administrar carro de compras**). Este problema se resolverá en un parche para Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto

Este artículo trata sobre un problema conocido en Commerce Admin al administrar una cotización B2B. No es posible añadir un producto configurable de **SKU** a la cita. Al hacer clic en **Añadir a cotización** botón, el **Cita** editar la página se atasca al cargarse y no se puede configurar el producto y guardar los cambios. Este problema también se produce en Administración al añadir un producto de **SKU** para agregar un producto a un pedido o agregue un producto **SKU** in **Cierre de compra avanzado** (**Administrador** > **Clientes** > **Todos los clientes** > **Edición de cliente** > **Administrar carro de compras**). Este problema se resolverá en un parche para Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Condiciones previas</u>

* Adobe Commerce 2.4.0 está instalado.
* B2B está instalado.
* Establezca las funciones B2B en **Habilitar compañía =**  *Sí* , **Habilitar catálogo compartido =**  *No* , y **Activar presupuesto B2B =**  *Sí*.
* Cree una cuenta de cliente.
* Cree una cuenta de compañía con el cliente creado anteriormente como administrador de la compañía.
* Cree un producto simple (Ejemplo: nombre &amp; **SKU** = TEST SIMPLE 1) que no está asignado a **Predeterminado (general)**.
* Pida al administrador de la empresa que solicite una cotización utilizando el producto simple creado anteriormente (Ejemplo: TEST SIMPLE 1).

<u>Pasos a seguir</u>

1. Vaya al panel de administración de Commerce.
1. Ir a **Ventas > Ofertas**.
1. Abra el **Cita**.
1. Haga clic en **Añadir producto por SKU** botón.
1. Introduzca el **SKU** de otro producto (Ejemplo: TEST SIMPLE 2) en la **Introducir SKU** campo de entrada.
1. Introduzca una cantidad válida en **Cant** campo de entrada.
1. Haga clic en **Añadir a cotización** botón.

<u>Resultados esperados</u>

* El **Productos no añadidos a la oferta** cuadrícula, que contiene el nombre y **SKU** del producto creado, aparece según lo esperado.
* Una vez configurado el producto, el administrador puede agregarlo al **Cita** haciendo clic en **Añadir productos al presupuesto** botón, como se esperaba.

<u>Resultados reales</u>

* El **Productos no añadidos a la oferta** cuadrícula, que contiene el nombre y **SKU** del producto creado, no aparece.
* El **Cita** página atascada cargando.

## Recomendación

En la actualidad, no hay solución para este problema con la edición de presupuestos B2B, pero para la gestión de pedidos y del carro de compras es posible seleccionar productos en la **Lista de productos** en lugar de agregarlas **SKU**. Habrá disponible un parche para resolver el problema para Adobe Commerce 2.4.1, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lectura relacionada

* [Problema conocido de Adobe Commerce 2.4.0: la actualización de las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensajes sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: error de visualización de pedidos](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
