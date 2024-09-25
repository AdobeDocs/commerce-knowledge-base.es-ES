---
title: Error al filtrar las solicitudes en el administrador
description: Este artículo proporciona un parche para el problema de Adobe Commerce, en el que se produce un error al intentar filtrar los pedidos en el Administrador por fecha, y se muestra el mensaje "Infracción de restricción de integridad 1052 Columna 'created_at' donde la cláusula es ambigua".
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Error al filtrar las solicitudes en el administrador

Este artículo proporciona un parche para el problema de Adobe Commerce en el que se produce un error al intentar filtrar los pedidos en el Administrador por fecha, y muestra el mensaje: *Infracción de restricción de integridad: 1052 Columna &#39;created_at&#39; donde la cláusula es ambigua*.

## Versiones afectadas

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7

## Problema

Si se filtran los pedidos en la Admin por fecha, se devuelve un error.

Exception.log muestra:

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>Pasos a seguir:</u>

1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
   * Establecer el orden de **[!UICONTROL Purchase Date Ascending]** en la cuadrícula, O
   * Definir **[!UICONTROL Purchase Date Filter]** en filtros.

1. Aparece un error: *Se produjo un error al procesar la vista predeterminada y se restauró el filtro a su estado original.*

## Causa

Hay un problema con los módulos [!DNL PayPal Braintree].

## Solución

Para resolver el problema, aplique el parche adjunto a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

El parche es compatible con todas las versiones y ediciones afectadas.

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en la base de conocimiento de soporte.
