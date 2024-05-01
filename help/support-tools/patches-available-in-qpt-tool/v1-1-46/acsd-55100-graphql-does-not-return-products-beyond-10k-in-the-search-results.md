---
title: "ACSD-55100: [!DNL GraphQL] no devuelve productos superiores a 10 000 en los resultados de búsqueda"
description: Aplique el parche ACSD-55100 para corregir el problema de Adobe Commerce en el que GraphQL no devuelve productos superiores a *10k* en los resultados de búsqueda.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL] no devuelve productos superiores a 10 000 en los resultados de búsqueda

El parche ACSD-55100 corrige el problema donde [!DNL GraphQL] no devuelve productos más allá de *10k* en los resultados de búsqueda. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 está instalado. El ID del parche es ACSD-55100. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL GraphQL] no devuelve productos más allá de *10k* en los resultados de búsqueda.

<u>Requisitos previos</u>:

En el caso de **[!DNL OpenSearch]**, asegúrese de que está utilizando la versión más reciente disponible.

Para resolver el problema del que se ha informado, se introduce la funcionalidad Punto en el tiempo, que está disponible después de **[!DNL OpenSearch]** 2.5.0 y requiere la versión 2.2 del `opensearch-project/opensearch-php` paquete.

Sin embargo, hay un conflicto con el `magento/magento-cloud-metapackage`, que especifica una dependencia de `opensearch-project/opensearch-php` que debería ser anterior a la versión 2.0.1.


Esta dependencia impide actualizar el [opensearch-project/opensearch-php] a la última versión 2.2.

Como resultado, el sistema encuentra el siguiente error y devuelve resultados nulos para los productos que exceden *10.000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

La dependencia existente dificulta la adición directa de una versión a `composer.json` y actualice el `opensearch-project/opensearch-php` a la versión 2.2.

Para resolver el problema, incluya la siguiente línea en su `composer.json` en el bloque requerido. Después, vuelva a implementar para actualizar el paquete problemático a la versión más reciente.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Pasos a seguir</u>:

1. Genere el catálogo con *15k* productos.
1. Envíe el [!DNL GraphQL]:

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Resultados esperados</u>:

Total_count = *15k*
Debería poder mostrar todos los productos.

<u>Resultados reales</u>:

Total_count = *10k*
No puede conseguir más productos para mostrar después de la *10k* lote.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
