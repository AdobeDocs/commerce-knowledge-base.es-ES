---
title: '''ACSD-56193: [!DNL Fastly] no se ha borrado la caché para la actualización del ensayo de contenido"'
description: Aplique el parche ACSD-56193 para solucionar el problema de Adobe Commerce donde la variable [!DNL Fastly] no se ha borrado la caché para la actualización del ensayo de contenido.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: d4bbfafa-2d24-44cf-a08b-f7dd9111a65b
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56193: [!DNL Fastly] no se ha borrado la caché para la actualización del ensayo de contenido

El parche ACSD-56193 corrige el problema en el que la variable [!DNL Fastly] no se ha borrado la caché para la actualización del ensayo de contenido. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 está instalado. El ID del parche es ACSD-56193. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El [!DNL Fastly/Varnish] no se ha borrado la caché para la actualización del ensayo de contenido

<u>Pasos a seguir</u>:

1. Instalación y configuración [!DNL Varnish] caché.
1. Cree un bloque estático con una actualización programada.
1. Cree una categoría que incruste el bloque estático.
1. Recupere el contenido de la categoría utilizando la siguiente consulta de GraphQL:

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Ejecute esta consulta varias veces y asegúrese de que la respuesta se almacena en caché en la [!DNL Varnish].
1. Ejecute el cron para aplicar el cambio programado.
1. Vuelva a ejecutar la consulta de GraphQL anterior.
1. Cree una nueva programación para el mismo bloque estático.
1. Repita los pasos numerados del 5 al 9.

<u>Resultados esperados</u>:

El contenido actualizado se devuelve después de que se ejecuten las actualizaciones programadas.

<u>Resultados reales</u>:

El contenido obsoleto se devuelve después de que se ejecuten las actualizaciones programadas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
