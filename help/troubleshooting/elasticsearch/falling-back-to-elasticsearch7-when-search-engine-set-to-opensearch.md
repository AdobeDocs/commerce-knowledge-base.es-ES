---
title: Volver a [!DNL Elasticsearch7] cuando el motor de búsqueda se estableció en [!DNL Opensearch]
description: Este artículo proporciona una solución para el problema cuando se produce un error *Volver a [!DNL Elasticsearch7]* cuando el motor de búsqueda se establece en [!DNL OpenSearch] en Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%
---
# Volver a [!DNL Elasticsearch7] cuando el motor de búsqueda se estableció en [!DNL Opensearch]

Este artículo proporciona una solución para el problema cuando se produce un error de *Retroceso a[!DNL Elasticsearch7]* cuando el motor de búsqueda se establece en [!DNL OpenSearch] en Adobe Commerce.

## Versiones afectadas

Adobe Commerce en la infraestructura en la nube
2.4.4 - 2.4.4-p12
2,4,5 - 2,4,5-p11

>[!NOTE]
>
>[!DNL OpenSearch] está disponible como motor de búsqueda a partir de Adobe Commerce 2.4.6, 2.4.5-p12, 2.4.4-p13.

## Problema

Ha establecido su **motor de búsqueda** en **[!DNL OpenSearch]**, pero observa este tipo de error en el archivo `var/log/support_report.log`:

`[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []`

<u>Pasos a seguir</u>:

1. Compruebe que [!DNL OpenSearch] está instalado ejecutando este comando: `curl 127.0.0.1:9200`<br>
Si indica *1.2.4*, entonces [!DNL OpenSearch] ya está instalado.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Compruebe el motor de búsqueda. Se mostrará [!DNL Elasticsearch7].

## Causa

Aunque su versión sí admite [!DNL OpenSearch], la aplicación solo reconocerá o aceptará [!DNL Elasticsearch7] como motor de búsqueda.

A partir de la versión 2.4.6 de Adobe Commerce, la aplicación se actualizó para permitir que [!DNL OpenSearch] se seleccionara como motor de búsqueda.
Si va a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** en un entorno que no está en la nube, podrá cambiar esta opción como se muestra en la **solución** que aparece a continuación.
(Nota: En un entorno de nube, este campo no se puede cambiar porque el motor de búsqueda está bloqueado en el archivo `app/etc/env.php`).

## Solución

Actualice la variable `SEARCH_CONFIGURATION` en el archivo `.magento.env.yaml` y asegúrese de que el **motor de búsqueda** está establecido en *[!DNL elasticsearch7]*.

## Lectura relacionada

[Configure el servicio OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html?lang=es) en la guía de Commerce en infraestructura de nube.
