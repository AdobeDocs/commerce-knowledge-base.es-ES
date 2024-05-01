---
title: '[!DNL Elasticsearch] se muestra como motor de búsqueda a pesar de que [!DNL OpenSearch] instalación'
description: Este artículo proporciona una solución para el problema donde [!DNL Elasticsearch] sigue mostrándose como el motor de búsqueda de Adobe Commerce en la nube incluso después de instalar o actualizar a [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1a36e74807e6d32b0810416b6fb61aeca6f9be94
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# [!DNL Elasticsearch] se muestra como motor de búsqueda a pesar de que [!DNL OpenSearch] instalación

Este artículo proporciona una solución para el problema donde [!DNL Elasticsearch] sigue mostrándose como el motor de búsqueda de Adobe Commerce en la nube incluso después de instalar o actualizar a [!DNL OpenSearch].

## Versiones afectadas

Adobe Commerce en la nube 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] está disponible como motor de búsqueda a partir de Adobe Commerce 2.4.6.

## Problema

[!DNL Elasticsearch] sigue mostrándose como el motor de búsqueda de Adobe Commerce en la nube incluso después de instalar o actualizar a [!DNL OpenSearch].

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Compruebe el motor de búsqueda. Se mostrará [!DNL Elasticsearch7].

## Causa

Adobe Commerce está codificado para especificar [!DNL Elasticsearch7] como motor de búsqueda.

## Solución

Para comprobar si [!DNL OpenSearch] se ha instalado, ejecute el siguiente comando:

**Método 1**:

* Ejecute el siguiente comando en el servidor: `curl 127.0.0.1:9200`. Debería volver [!DNL OpenSearch] con su versión.

**Método 2**:

* Utilice el siguiente comando en la CLI de la nube de Magento: `magento-cloud relationships -p <project_id>`. Después de usar el comando, busque [!DNL OpenSearch].

## Lectura relacionada

[Configuración del servicio OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) en la guía Commerce sobre infraestructura en la nube.
