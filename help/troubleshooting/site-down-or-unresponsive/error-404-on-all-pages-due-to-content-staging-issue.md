---
title: Error 404 en todas las páginas debido a un problema con el ensayo de contenido
description: Este artículo proporciona una corrección para el problema de infraestructura de Adobe Commerce local y Adobe Commerce en la nube en el que se obtiene un error 404 al acceder a cualquier página de tienda o al administrador de Commerce.
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Error 404 en todas las páginas debido a un problema con el ensayo de contenido

Este artículo proporciona una corrección para el problema de infraestructura de Adobe Commerce local y Adobe Commerce en la nube en el que se obtiene un error 404 al acceder a cualquier página de tienda o al administrador de Commerce.

## Productos y versiones afectados

* Adobe Commerce local 2.2.x, 2.3.x
* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x

## Problema

>[!NOTE]
>
>Este artículo no se aplica a la situación en la que se obtiene un error 404 al intentar [previsualización de la actualización de ensayo](https://docs.magento.com/user-guide/cms/content-staging-scheduled-update.html#preview-the-scheduled-change). Si encuentra ese problema, abra una [ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

El acceso a cualquier página de la tienda o al administrador provoca el error 404 (la página &quot;¡Uy!, nuestro mal...&quot;) después de realizar operaciones con actualizaciones programadas para los recursos de contenido de la tienda mediante [Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) (actualizaciones para los recursos de contenido de tienda programados con la variable [Magento\_Módulo de ensayo](https://developer.adobe.com/commerce/php/module-reference/)). Por ejemplo, es posible que haya eliminado un producto con una actualización programada o que haya eliminado la fecha de finalización de la actualización programada.

Un recurso de contenido de tienda incluye:

* Product
* Categoría
* Regla de precio de catálogo
* Regla de precio del carro
* Página de CMS
* Bloque CMS
* Widget

Algunos escenarios se analizan en la sección Causa a continuación.

## Causa

El `flag` La tabla de la base de datos (DB) contiene vínculos no válidos a `staging_update` tabla.

El problema está relacionado con el Ensayo de contenido. A continuación se presentan dos escenarios particulares; tenga en cuenta que podría haber más situaciones que pongan en déclencheur el problema.

**Escenario 1:** Eliminar un recurso de contenido de tienda que:

* tiene una actualización programada con el ensayo de contenido
* la actualización tiene una fecha de finalización (es decir, la fecha de caducidad después de la cual el recurso actualizado vuelve a su versión anterior)
* la fecha de finalización de la actualización es anterior

Al mismo tiempo, es posible que el problema no se produzca si un recurso eliminado no tiene fecha de finalización para la actualización programada.

**Escenario 2:** Eliminar la fecha/hora de finalización de una actualización programada.

### Identificar si el problema está relacionado

Para identificar si el problema que está experimentando es el descrito en este artículo, ejecute la siguiente consulta de base de datos:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Si la consulta devuelve una tabla donde `update_exists` El valor es &quot;0&quot; y, a continuación, un vínculo no válido al `staging_update` existe en la base de datos y los pasos descritos en la [Sección Solución](#solution) ayudará a resolver el problema. A continuación se muestra un ejemplo del resultado de la consulta con `update_exists` valor igual a &quot;0&quot;:

![update_exists_0.png](assets/update_exists_0.png)

Si la consulta devuelve una tabla donde `update_exists` el valor es &quot;1&quot; o un resultado vacío, significa que el problema no está relacionado con las actualizaciones de ensayo. A continuación se muestra un ejemplo del resultado de la consulta con `update_exists` valor igual a 1:

![updates_exist_1.png](assets/updates_exist_1.png)

En este caso, puede hacer referencia a la variable [Solucionador de problemas de Site Down](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) para solucionar problemas.

## Solución

1. Ejecute la siguiente consulta para eliminar el vínculo no válido a `staging_update` tabla:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Espere a que se ejecute el trabajo cron (se ejecuta en hasta cinco minutos si está configurado correctamente) o ejecútelo manualmente si no tiene cron configurado.

El problema debe resolverse directamente después de corregir el vínculo no válido. Si el problema persiste, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
