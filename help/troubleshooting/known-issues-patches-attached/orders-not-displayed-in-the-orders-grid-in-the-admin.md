---
title: Pedidos no mostrados en la cuadrícula Pedidos del administrador
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.1 relacionado con los pedidos que no se muestran en la cuadrícula Pedidos del administrador de Commerce.
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Pedidos no mostrados en la cuadrícula Pedidos del administrador

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.1 relacionado con los pedidos que no se muestran en la cuadrícula Pedidos del administrador de Commerce.

## Problema

En Adobe Commerce 2.2.1 con la extensión B2B instalada, los pedidos creados en la tienda por un cliente registrado no se muestran en la lista de pedidos de la cuenta del cliente en el administrador de Commerce. En el registro de depuración (`./var/log/debug.log`), se registra el siguiente error:

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>Requisitos previos</u>:

El catálogo de la tienda contiene productos, no datos de muestra de Adobe Commerce, y se instala la extensión B2B.

<u>Pasos a seguir</u>:

1. Vaya a la tienda y cree una cuenta de cliente.
1. Añada un producto al carro de compras, complete el cierre de compra y envíe un pedido.
1. Inicie sesión en Admin.
1. Vaya a **Clientes,** luego elija **Todos los clientes**.
1. Para el cliente recién creado, haga clic en **Editar**.
1. Clic **Pedidos** en el panel de la izquierda.

<u>Resultado esperado</u>:

El pedido enviado recientemente aparece en la cuadrícula.

<u>Resultado real</u>:

La cuadrícula Pedidos no se muestra. En su lugar, aparece una página en blanco.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-7868\_EE\_2.2.1\_v1\_composer.patch](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce local 2.2.1

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en la infraestructura en la nube de 2.2.0 a 2.2.3
* Adobe Commerce local 2.2.0 y 2.2.2 a 2.2.3

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte, para obtener instrucciones.

## Archivos adjuntos
