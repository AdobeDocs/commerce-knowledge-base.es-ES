---
title: Error 404 en todas las páginas debido a un problema con el ensayo de contenido
description: Este artículo proporciona una corrección para el problema de infraestructura de Adobe Commerce local y Adobe Commerce en la nube en el que se obtiene un error 404 al acceder a cualquier página de tienda o al [!UICONTROL Commerce Admin].
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: 48f06a90108842e00745b75db2f56a320704faf5
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Error 404 en todas las páginas debido a un problema con el ensayo de contenido

Este artículo proporciona una corrección para el problema de infraestructura de Adobe Commerce local y Adobe Commerce en la nube en el que se obtiene un error 404 al acceder a cualquier página de tienda o al [!UICONTROL Commerce Admin].

## Productos y versiones afectados

* Adobe Commerce local 2.2.x, 2.3.x
* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x

## Problema

>[!NOTE]
>
>Este artículo no se aplica a la situación en la que recibes un error 404 al intentar [previsualizar la actualización de ensayo](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/guide-overview#preview-the-scheduled-change). Si encuentra ese problema, abra un [ticket de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

El acceso a cualquier página de la tienda o al administrador provoca el error 404 (la página &quot;¡Uy!, nuestra página es incorrecta...&quot;) después de realizar operaciones con actualizaciones programadas para los recursos de contenido de la tienda mediante [Ensayo de contenido](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) (actualizaciones para los recursos de contenido de la tienda programados mediante el [módulo Magento\_Staging](https://developer.adobe.com/commerce/php/module-reference/)). Por ejemplo, es posible que haya eliminado un producto con una actualización programada o que haya eliminado la fecha de finalización de la actualización programada.

Un recurso de contenido de tienda incluye:

* Product
* Categoría
* Regla de precio de catálogo
* Regla de precio del carro
* Página de CMS
* Bloque de CMS
* Widget

Algunos escenarios se analizan en la sección Causa a continuación.

## Causa

La tabla `flag` de la base de datos (DB) contiene vínculos no válidos a la tabla `staging_update`.

El problema está relacionado con el Ensayo de contenido. A continuación se presentan dos escenarios particulares; tenga en cuenta que podría haber más situaciones que pongan en déclencheur el problema.

**Escenario 1:** Se está eliminando un recurso de contenido de almacén que:

* tiene una actualización programada con el ensayo de contenido
* la actualización tiene una fecha de finalización (es decir, la fecha de caducidad después de la cual el recurso actualizado vuelve a su versión anterior)
* la fecha de finalización de la actualización es anterior

Al mismo tiempo, es posible que el problema no se produzca si un recurso eliminado no tiene fecha de finalización para la actualización programada.

**Escenario 2:** al eliminar la fecha/hora de finalización de una actualización programada.

### Identificar si el problema está relacionado

Para identificar si el problema que está experimentando es el descrito en este artículo, ejecute la siguiente consulta de base de datos:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Si la consulta devuelve una tabla donde el valor `update_exists` es &quot;0&quot;, existe un vínculo no válido a la tabla `staging_update` en la base de datos y los pasos descritos en la [sección de soluciones](#solution) ayudarán a resolver el problema. A continuación se muestra un ejemplo del resultado de la consulta con un valor de `update_exists` igual a &quot;0&quot;:

![update_exists_0.png](assets/update_exists_0.png)

Si la consulta devuelve una tabla en la que el valor `update_exists` es &quot;1&quot; o un resultado vacío, significa que el problema no está relacionado con las actualizaciones de ensayo. A continuación se muestra un ejemplo del resultado de la consulta con un valor de `update_exists` igual a &quot;1&quot;:

![actualizaciones_existen_1.png](assets/updates_exist_1.png)

En este caso, puede consultar [Solucionador de problemas de caída del sitio](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27152) para obtener ideas sobre la solución de problemas.

## Solución

1. Ejecute la siguiente consulta para eliminar el vínculo no válido a la tabla `staging_update`:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Espere a que se ejecute el trabajo de [!DNL cron] (se ejecuta en cinco minutos si está configurado correctamente) o ejecútelo manualmente si no ha configurado [!DNL cron].

El problema debe resolverse directamente después de corregir el vínculo no válido. Si el problema persiste, [envíe un vale de soporte técnico](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

## Lectura relacionada

[Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
