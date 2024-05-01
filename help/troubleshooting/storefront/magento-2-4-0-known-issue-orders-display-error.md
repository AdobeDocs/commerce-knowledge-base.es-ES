---
title: "Problema conocido de Adobe Commerce 2.4.0: error de visualización de pedidos"
description: '''Este artículo proporciona una solución para un problema conocido en Adobe Commerce por un error de visualización de pedidos. Cuando los clientes que iniciaron sesión revisan sus pedidos en el menú **Mi cuenta** (**Mi cuenta &gt; Mis pedidos**), la cuadrícula de pedidos no puede cambiar el número de pedidos por página a 20 desde la página 2 cuando hay 11 pedidos. Además, si hay más pedidos de los configurados para mostrar por página, al navegar a la última página con pedidos, al cambiar el número de pedidos mostrados por página se produce el mensaje de error: * No ha realizado ningún pedido*. Este problema se resolverá en Adobe Commerce 2.4.1."'
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Problema conocido de Adobe Commerce 2.4.0: error de visualización de pedidos

Este artículo proporciona una solución para un problema conocido en Adobe Commerce por un error de visualización de pedidos. Cuando los clientes inician sesión, revisan sus pedidos en **Mi cuenta** menú (**Mi cuenta > Mis pedidos**), la cuadrícula de pedidos no puede cambiar el número de pedidos por página a 20 desde la página 2 cuando hay 11 pedidos. Además, si hay más pedidos de los configurados para mostrar por página, al navegar a la última página con pedidos, al cambiar el número de pedidos mostrados por página se produce el mensaje de error: *No ha realizado ningún pedido*. Este problema se resolverá en Adobe Commerce 2.4.1.

## Productos y versiones afectados

* Adobe Commerce local 2.4.0
* Adobe Commerce en infraestructura en la nube 2.4.0

## Problema

<u>Requisitos previos</u>

* Adobe Commerce 2.4.0 está instalado.
* Cree al menos una categoría y un producto simple.

<u>Pasos a seguir</u>

1. Cree 11 pedidos con productos.
1. Ir a **Mi cuenta**.
1. Ir a **Mis pedidos**.
1. Haga clic en la segunda página para mostrar el undécimo pedido en la cuadrícula de pedidos.
1. Seleccionar **Mostrar = 20 por página** en el menú desplegable.

<u>Resultado esperado</u>

Los 11 pedidos se muestran en la primera página, según lo esperado.

<u>Resultado real</u>

El *No ha realizado ningún pedido* se muestra un mensaje de error.

## Solución

La solución consiste en que el comprador vuelva a abrir **Mis pedidos** y, a continuación, la lista de pedidos se mostrará correctamente. El problema se solucionará en la próxima versión, Adobe Commerce 2.4.1, cuyo lanzamiento está programado para el cuarto trimestre de 2020.

## Lecturas relacionadas en nuestra base de conocimiento de soporte

* [Problema conocido de Adobe Commerce 2.4.0: la actualización en las actividades del cliente no funciona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema conocido de Adobe Commerce 2.4.0: visualización de datos de mensajes sin procesar en la tienda](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema conocido de Adobe Commerce 2.4.0: Las tasas de impuestos de exportación no funcionan](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [El administrador de Adobe Commerce 2.4.0 B2B no puede añadir un producto configurable al presupuesto](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
