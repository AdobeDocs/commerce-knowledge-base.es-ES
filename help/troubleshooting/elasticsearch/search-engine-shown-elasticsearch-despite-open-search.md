---
title: '[!DNL Elasticsearch] se muestra como motor de búsqueda a pesar de que [!DNL OpenSearch] instalación'
description: Este artículo proporciona una solución para el problema donde [!DNL Elasticsearch] sigue mostrándose como el motor de búsqueda de Adobe Commerce en la nube incluso después de instalar o actualizar a [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
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

Esto no debe confundirse con la versión instalada del servicio. La aplicación solo reconoce [!DNL Elasticsearch7] como motor de búsqueda, pero no [!DNL OpenSearch], aunque utilice el subyacente [!DNL OpenSearch] como motor en el servidor.

## Solución

Para comprobar si [!DNL OpenSearch] se ha instalado, ejecute el siguiente comando:

**Método 1**:

* Ejecute el siguiente comando en el servidor: `curl 127.0.0.1:9200`. Debería volver [!DNL OpenSearch] con su versión.

Ejemplo:

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**Método 2**:

* Utilice el siguiente comando en la CLI de la nube de Magento: `magento-cloud relationships -p <project_id>`. Después de usar el comando, busque [!DNL OpenSearch].

## Lectura relacionada

[Configuración del servicio OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) en la guía Commerce sobre infraestructura en la nube.
