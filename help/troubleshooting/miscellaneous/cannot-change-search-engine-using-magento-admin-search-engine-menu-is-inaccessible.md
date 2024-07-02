---
title: No se puede cambiar el motor de búsqueda mediante la administración de Commerce (no se puede acceder al menú del motor de búsqueda)
description: Este artículo proporciona una solución para cambiar el motor de búsqueda de Adobe Commerce mediante el administrador de Commerce si el campo Motor de búsqueda no se muestra o la casilla de verificación Usar valor del sistema aparece atenuada y no se puede acceder a ella.
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: e9f009cf4e072dcd9784693c10a4c16746af3cc5
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# No se puede cambiar el motor de búsqueda mediante la administración de Commerce (no se puede acceder al menú del motor de búsqueda)

>[!WARNING]
>
> [El motor de búsqueda del catálogo MySQL se eliminará en Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Debe tener el host de Elasticsearch configurado antes de instalar la versión 2.4.0.
> 
> Consulte:
> [Elasticsearch de instalación y configuración](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
> [Instalar y configurar Opensearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [Instalar y configurar Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)

Este artículo proporciona una solución para cambiar el motor de búsqueda de Adobe Commerce mediante el administrador de Commerce si la variable **Motor de búsqueda** no se muestra para que la variable **Usar valor del sistema** la casilla de verificación aparece atenuada y no se puede acceder a ella.

En este artículo:

* [Versiones afectadas](#affected-versions)
* [Cambiar el motor de búsqueda mediante el administrador de Commerce (pasos)](#change-search-engine-using-magento-admin-steps)
* [Problemas con Adobe Commerce local](#magento-commerce-on-premise)
* [Adobe Commerce en la infraestructura en la nube](#magento-commerce-cloud)

## Versiones afectadas

* Adobe Commerce local: 2.4.X
* Adobe Commerce en la infraestructura en la nube:
   * Versión: 2.4.X
   * Arquitectura de plan Starter y Pro
* MySQL, Elasticsearch, Opensearch, Live Search: todas las versiones compatibles

## Cambiar el motor de búsqueda mediante el administrador (pasos)

1. Inicie sesión en Admin como administrador.
1. En la barra lateral izquierda de Administración, haga clic en **Tiendas**. A continuación, en **Configuración**, elija **Configuración**.
1. En el panel de la izquierda debajo de **Catálogo,** escoger **Catálogo**.
1. Expanda el **Búsqueda en catálogo** sección.    ![catalog_menu.png](assets/catalog_menu.png)
1. Vaya a la **Motor de búsqueda** y eliminar la selección de la **Usar valor del sistema** casilla de verificación
1. Haga clic en **Motor de búsqueda** y seleccione una de las opciones disponibles.    ![search_engine_menu.png](assets/search_engine_menu.png)
1. Clic **Guardar configuración** en la esquina superior derecha de la página.

## Problemas con Adobe Commerce local

### Problema 1: No se muestra el campo del motor de búsqueda

Al acceder a **Búsqueda en catálogo** , la sección **Motor de búsqueda** El menú no se muestra en absoluto.

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### Causa: la vista de la tienda no es una configuración predeterminada

La vista de tienda del administrador se ha establecido en cualquier valor distinto de *Configuración predeterminada*.

El motor de búsqueda es una configuración global establecida en el nivel de aplicación, no en el ámbito de la tienda. Las tiendas dentro de una aplicación de Adobe Commerce no pueden utilizar motores de búsqueda diferentes.

### Solución: establezca la vista de la tienda en la configuración predeterminada

1. Inicie sesión en Admin como administrador.
1. En la barra lateral izquierda de Administración, haga clic en **Tiendas**. A continuación, en **Configuración**, elija **Configuración**.
1. En la esquina superior izquierda, haga clic **Vista de tienda** y elija *Configuración predeterminada*.
1. Clic **OK** en el cuadro de diálogo de confirmación para aprobar el cambio de vista de la tienda.

![change_store_view.png](assets/change_store_view.png)

**Documentación relacionada:** [Cambio de ámbito](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope) en nuestra guía del usuario.

### Problema 2: No se puede desmarcar &quot;Usar valor del sistema&quot;

Al acceder a **Búsqueda en catálogo** de Admin, la sección **Usar valor del sistema** La casilla de verificación de está atenuada, por lo que no se puede quitar la selección de la casilla de verificación para cambiar posteriormente el motor de búsqueda.

### Causa

El motor de búsqueda predeterminado se ha configurado en el nivel de configuración de la aplicación en `app/etc/env.php` o `app/etc/config.php` y, por lo tanto, no se pueden cambiar con el Administrador.

Ejemplo de la sección con la configuración predeterminada del motor de búsqueda:

```php
'system'=>
array (
'default'=>
array (
'catalog'=>
array (
'search'=>
array (
'engine'=>'mysql',
),
),
),
),
```

### Solución

Elimine la sección con la configuración predeterminada del motor de búsqueda de `app/etc/env.php` o el `app/etc/config.php` archivos de configuración.

### Artículos relacionados en nuestra documentación para desarrolladores

[Archivos de configuración de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html) en la Guía de configuración de Adobe Commerce

## Adobe Commerce en la infraestructura en la nube

El cambio de motores de búsqueda mediante Admin no está disponible en Adobe Commerce en la infraestructura en la nube debido a la forma en que se ha organizado esta.

Durante el proceso de implementación, los scripts de implementación de Adobe Commerce en la nube comprueban si se ha declarado Elasticsearch en la `MAGENTO_CLOUD_RELATIONSHIPS` variable. Si se declara, el Elasticsearch se selecciona como motor de búsqueda activo y se configura automáticamente; la variable [Motor de búsqueda MySQL](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) se vuelve inaccesible en el Administrador. Si no se ha declarado la relación de Elasticsearch, MySQL se establece como activo y Elasticsearch se vuelve inaccesible.

No se recomienda editar la variable `app/etc/env.php` o el `app/etc/config.php` archivos de configuración directamente en su entorno de nube; es por eso que cambiar estos archivos para que el motor del Elasticsearch se muestre en Admin (la solución que recomendamos en la sección anterior) no es aplicable a su proyecto de nube.

### Cambiar el motor de búsqueda en los entornos de ensayo y producción

Antes de cambiar el motor de búsqueda de MySQL a Elasticsearch en los entornos de ensayo y producción, asegúrese de haber cambiado anteriormente [envió una solicitud de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) se ha resuelto correctamente la solicitud para habilitar el Elasticsearch en el entorno y el ticket.

Para cambiar el motor de búsqueda utilizado en los entornos de ensayo y producción, cambie el `SEARCH_CONFIGURATION` variable de entorno en su `.magento.env.yaml` en su entorno local y, a continuación, inserte cambios en los entornos de integración y ensayo/producción para que los cambios surtan efecto.

Si cambia al Elasticsearch 7, la variable SEARCH\_CONFIGURATION en el `.magento.env.yaml` el archivo puede tener el siguiente aspecto:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Si cambia a [Opensearch (en 2.4.6 y versiones posteriores)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search) la variable SEARCH\_CONFIGURATION en el `.magento.env.yaml` el archivo puede tener el siguiente aspecto:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: opensearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Si es usted [cambiar a Live Search](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch), la variable SEARCH\_CONFIGURATION en el `.magento.env.yaml` el archivo puede tener el siguiente aspecto:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: livesearch
```

### Documentación relacionada

#### Base de conocimiento de asistencia

* [Habilitar Elasticsearch en la nube](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### Documentación para desarrolladores

* [Configuración del servicio de Elasticsearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [Creación e implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) (documentación sobre el `.magento.env.yaml` archivo de configuración)
* [Implementación de variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) ([sección SEARCH\_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration))
* [Servicios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) (documentación sobre el `.magento/services.yaml` archivo de configuración)
* [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)
