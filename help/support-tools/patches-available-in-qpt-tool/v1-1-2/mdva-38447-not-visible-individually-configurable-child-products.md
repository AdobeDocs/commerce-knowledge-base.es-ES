---
title: '"MDVA-38447: Los productos secundarios configurables "no visibles individualmente" se devuelven en la respuesta de GraphQL y en la consulta MySQL lenta"'
description: El parche de MDVA-38447 Adobe Commerce corrige el problema en el que los productos secundarios configurables "No visibles individualmente" se devuelven en la respuesta de GraphQL y ralentizan la consulta MySQL para productos de GraphQL con el filtro de categoría. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-38447. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-38447: Los productos secundarios configurables &quot;no visibles individualmente&quot; se devuelven en la respuesta de GraphQL y en la consulta MySQL lenta

El parche de MDVA-38447 Adobe Commerce corrige el problema en el que los productos secundarios configurables &quot;No visibles individualmente&quot; se devuelven en la respuesta de GraphQL y ralentizan la consulta MySQL para productos de GraphQL con el filtro de categoría. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-38447. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos secundarios configurables &quot;No visibles individualmente&quot; se devuelven en la respuesta de GraphQL y en la consulta lenta de MySQL para la consulta de productos de GraphQL con el filtro de categoría.

<u>Requisitos previos</u>:

Deben instalarse los módulos B2B.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con productos simples configurados en **No visible individualmente**.
1. Ejecute **reindexación completa**.
1. Ejecutar una **consulta GraphQL** como:

<pre>query getFilteredProducts()
  $filter: ProductAttributeFilterInput.
  $sort: ProductAttributeSortInput.
  $search: String
  $pageSize: Int!
  $currentPage: Int!
) {
  products()
    filter: $filter
    sort: $sort
    buscar: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) {
    total_count
    page_info {
      total_pages
      current_page
      page_size
    }
    elementos {
      name
      sku
    }
  }
}</pre>

Variables:

<pre>{"filter":{"user_group":{"eq":""}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Resultados esperados</u>:

Los productos con visibilidad definida como &quot;No visible individualmente&quot; no se devolverán como respuesta.

<u>Resultados reales</u>:

Los productos con la visibilidad configurada como &quot;No visible individualmente&quot; se devuelven como respuesta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre parches de calidad para Adobe Commerce, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
