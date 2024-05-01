---
title: Error de Adobe Commerce 2.4.6 al realizar la solicitud desde el panel de administración
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.4.6 cuando se queda atascado en la selección de la tienda después de realizar un pedido desde el Panel de administración de Commerce.
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Error de Adobe Commerce 2.4.6 al realizar la solicitud desde el panel de administración

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.4.6 cuando se queda atascado en la selección de la tienda después de realizar un pedido desde el Panel de administración de Commerce.

## Problema

Al realizar un pedido desde el panel de administración, se queda atascado en la selección de la tienda.

<u>Pasos a seguir</u>

1. Ir a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** y seleccione un cliente para crear un pedido.
2. Seleccione la tienda para realizar el pedido desde la pantalla del selector de tienda.

<u>Resultado esperado</u>

Después de seleccionar la tienda, puede completar el pedido.

<u>Resultado real:</u>

Después de seleccionar la tienda, se le redirige a la página de selección de tienda y no puede crear un pedido.

## Parche

Haga clic en el siguiente enlace para descargar el parche.

[Descargar ACSD-52277_2.4.6.patch](assets/ACSD-52277_2.4.6.patch.zip)

### Versiones de Adobe Commerce compatibles

El parche se ha creado para y es compatible con Adobe Commerce en la infraestructura en la nube y con Adobe Commerce local 2.4.6 y 2.4.6-p1.

## Cómo aplicar el parche

* Para obtener instrucciones sobre la aplicación de parches para Adobe Commerce en la infraestructura en la nube, consulte [Aplicar parches](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en nuestra Guía de infraestructura en la nube de Commerce.
* Para obtener instrucciones sobre la aplicación de parches para Adobe Commerce local, consulte [Aplicar parches](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer) en nuestra Guía de actualización de Commerce.
