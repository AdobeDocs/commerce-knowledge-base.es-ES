---
title: "ACSD-49973: rendimiento mejorado al recuperar productos agrupados mediante  [!DNL GraphQL]"
description: Aplique el parche ACSD-49973 para corregir el problema de Adobe Commerce donde se produce una degradación del rendimiento al recuperar productos agrupados mediante  [!DNL GraphQL].
exl-id: 7d7fce0f-40f9-4dec-aee7-1014690ccd7c
feature: GraphQL, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-49973: rendimiento mejorado al recuperar productos agrupados mediante [!DNL GraphQL]

El parche ACSD-49973 mejora el rendimiento al recuperar productos agrupados mediante [!DNL GraphQL]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. El ID del parche es ACSD-49973. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce una degradación del rendimiento al recuperar productos agrupados mediante [!DNL GraphQL].

<u>Requisitos previos</u>:

Cree 2000 paquetes de productos usando [Performance toolkit](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html?lang=es).

<u>Pasos a seguir</u>:

1. Habilitar el registrador de consultas [!DNL DB]:

   ```
   bin/magento dev:query-log:enable
   ```

1. Ejecute la siguiente consulta [!DNL GraphQL]:

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

1. Buscar solicitudes en la tabla `catalog_product_bundle_selection` de `var/log/db.log`.

<u>Resultados esperados</u>:

Las solicitudes para la tabla `catalog_product_bundle_selection` no deben estar presentes en `var/log/db.log`.

<u>Resultados reales</u>:

Hay 2000 solicitudes a `catalog_product_bundle_selection` tabla que se activan al mismo tiempo, lo que provoca una degradación del rendimiento.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
