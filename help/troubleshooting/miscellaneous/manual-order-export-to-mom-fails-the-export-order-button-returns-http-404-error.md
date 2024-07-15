---
title: La exportación manual de pedidos a MOM falla. El botón Exportar pedido devuelve el error HTTP 404
description: En este artículo se explica cómo solucionar un problema por el que, al intentar exportar una solicitud a un Magento Order Management (MOM) haciendo clic en el botón **Exportar pedido** en la vista de pedidos del administrador de Commerce, se devuelve un error " *404 Página no encontrada*".
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# La exportación manual de pedidos a MOM falla. El botón Exportar pedido devuelve el error HTTP 404

Este artículo explica cómo solucionar un problema por el cual al intentar exportar una solicitud al Magento Order Management (MOM) haciendo clic en el botón **Exportar pedido** en la vista de pedidos del administrador de Commerce, se devuelve un error de &quot;*404 página no encontrada*&quot;.

## Productos y versiones afectados

* Adobe Commerce 2.2.x, 2.3.x
* Conector MOM 2.3.0, 2.4.0, 3.2.0, 3.3.0

## Problema

<u>Pasos a seguir:</u>:

1. En el Administrador de Commerce, haga clic en **Ventas > Pedidos**.
1. Haga clic en el botón **Crear nuevo pedido**.
1. Selecciona un usuario, añade un artículo, selecciona las formas de pago y envío y luego pulsa el botón **Enviar pedido**.
1. Haga clic en el botón **Exportar pedido** y, a continuación, **Aceptar**.

<u>Resultado esperado</u>:

El pedido se envía a MOM.

<u>Resultado real</u>:

Se muestra una página de &quot; *404 error: página no encontrada* &quot;.

## Solución

* Actualice el conector MOM a 3.4.0 para Adobe Commerce 2.3.x o el conector MOM 2.5 para Adobe Commerce 2.2.x.
* Si actualizar el conector MOM no es una opción, puede exportar el pedido al Magento Order Management mediante el comando CLI:

```bash
$bin/magento oms:orders:sync
```

## Lectura relacionada

[Documentación técnica del Magento Order Management](https://omsdocs.magento.com/en/)
