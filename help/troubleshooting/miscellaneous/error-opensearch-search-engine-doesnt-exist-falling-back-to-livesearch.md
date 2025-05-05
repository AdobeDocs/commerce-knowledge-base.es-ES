---
title: Error [!DNL opensearch] el motor de búsqueda no existe. Volviendo a  [!DNL livesearch].
description: Este artículo proporciona una solución al problema donde se ve el error "Error- [!DNL opensearch] el motor de búsqueda no existe. Volver a  [!DNL livesearch].&grave;, en Adobe Commerce en la infraestructura en la nube.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Error [!DNL opensearch]. El motor de búsqueda no existe. Volviendo a [!DNL livesearch].

Este artículo proporciona una solución al problema donde se muestra el error: *Error: [!DNL opensearch] el motor de búsqueda no existe. Volviendo a [!DNL livesearch].* en Adobe Commerce en la infraestructura de nube donde se usa [!DNL Live Search].

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones
* [!DNL Live Search] está instalado y en uso

## Problema

El siguiente mensaje se muestra en los registros (y se puede observar en [!DNL New Relic]):
*Error: el motor de búsqueda [!DNL opensearch] no existe. Volviendo a [!DNL livesearch].*

## Solución

1. Modifique el archivo `.magento.env.yaml`.
1. Busque las líneas siguientes:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Si no tiene estas líneas, agréguelas al archivo `.magento.env.yaml`.
1. Si existen estas líneas, **modifique el motor** de *[!DNL opensearch]* a *[!DNL livesearch]*.
1. Confirme el cambio y vuelva a implementar.

## Lectura relacionada

* [Instalar [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) en nuestra Guía de Live Search
