---
title: Volver a caer en [!DNL Elasticsearch7] cuando el motor de búsqueda se establece en [!DNL Opensearch]
description: Este artículo proporciona una solución al problema cuando un *Volver a [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] en Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Volver a caer en [!DNL Elasticsearch7] cuando el motor de búsqueda se establece en [!DNL Opensearch]

Este artículo proporciona una solución para el problema cuando una *Volver a caer en[!DNL Elasticsearch7]* se produce un error cuando el motor de búsqueda está configurado en [!DNL OpenSearch] en Adobe Commerce.

## Versiones afectadas

Adobe Commerce en infraestructura en la nube 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] está disponible como motor de búsqueda a partir de Adobe Commerce 2.4.6.

## Problema

Usted establece su **motor de búsqueda** hasta **[!DNL OpenSearch]**, pero consulte este tipo de error en la `var/log/support_report.log` archivo:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Pasos a seguir</u>:

1. Compruebe que [!DNL OpenSearch] se instala ejecutando este comando: `curl 127.0.0.1:9200`<br>
Si indica *1.2.4*, entonces [!DNL OpenSearch] ya está instalado.
1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Compruebe el motor de búsqueda. Se mostrará [!DNL Elasticsearch7].

## Causa

Aunque su versión sí admite [!DNL OpenSearch], la aplicación solo reconocerá/aceptará [!DNL Elasticsearch7] como motor de búsqueda.

A partir de la versión 2.4.6 de Adobe Commerce, la aplicación se actualizó para permitir [!DNL OpenSearch] para que se seleccione como motor de búsqueda.
Si va a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** en un entorno que no sea de nube, podrá cambiar esta opción como se muestra en la **Solución** más abajo.
(Nota: En un entorno de nube, este campo no se puede cambiar porque el motor de búsqueda está bloqueado en `app/etc/env.php` file.)

## Solución

Actualice el `SEARCH_CONFIGURATION` en la variable `.magento.env.yaml` , y asegúrese de que la variable **motor de búsqueda** se establece en *[!DNL elasticsearch7]*.

## Lectura relacionada

[Configuración del servicio OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) en la guía Commerce sobre infraestructura en la nube.
