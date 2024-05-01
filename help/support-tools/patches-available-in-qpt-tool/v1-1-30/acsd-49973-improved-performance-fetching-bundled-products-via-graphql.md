---
title: '"ACSD-49973: rendimiento mejorado al recuperar productos agrupados mediante [!DNL GraphQL]'''
description: Aplique el parche ACSD-49973 para solucionar el problema de Adobe Commerce donde se produce una degradación del rendimiento al recuperar productos agrupados mediante [!DNL GraphQL].
exl-id: 7d7fce0f-40f9-4dec-aee7-1014690ccd7c
feature: GraphQL, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-49973: rendimiento mejorado al recuperar productos agrupados mediante [!DNL GraphQL]

El parche ACSD-49973 mejora el rendimiento al recuperar productos agrupados mediante [!DNL GraphQL]. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. El ID del parche es ACSD-49973. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La degradación del rendimiento se produce al recuperar productos agrupados mediante [!DNL GraphQL].

<u>Requisitos previos</u>:

Crear 2000 paquetes de productos utilizando [Kit de herramientas de rendimiento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html).

<u>Pasos a seguir</u>:

1. Habilite la [!DNL DB] registrador de consultas:

   ```
   bin/magento dev:query-log:enable
   ```

1. Ejecute lo siguiente [!DNL GraphQL] consulta:

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Marque `var/log/db.log` para solicitudes a `catalog_product_bundle_selection` tabla.

<u>Resultados esperados</u>:

Solicitudes a `catalog_product_bundle_selection` no debe estar presente en el `var/log/db.log`.

<u>Resultados reales</u>:

Hay 2000 solicitudes para `catalog_product_bundle_selection` que se activan al mismo tiempo, lo que provoca una degradación del rendimiento.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
