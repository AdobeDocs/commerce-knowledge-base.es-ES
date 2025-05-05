---
title: "MDVA-40120: La ordenación DESC/ASC del producto GraphQL no funciona"
description: El parche MDVA-40120 resuelve el problema en el que la clasificación de GraphQL por DESC/ASC no funciona con productos que tienen la misma relevancia o precio. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. El ID del parche es MDVA-40120. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: f04373d6-d3e8-47ba-9261-87fad8dff327
feature: GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-40120: La ordenación DESC/ASC del producto de GraphQL no funciona

El parche MDVA-40120 resuelve el problema en el que la clasificación de GraphQL por DESC/ASC no funciona con productos que tienen la misma relevancia o precio. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. El ID del parche es MDVA-40120. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisitos previos</u>:

Cree algunos productos diferentes con el mismo precio.

<u>Pasos a seguir</u>:

1. Ejecute la siguiente consulta de GraphQL:
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. Compruebe la respuesta.
1. Cambie el criterio de ordenación de **ASC** a **DESC** en la consulta de GraphQL:
   <pre>
    <code class="language-graphql">
    &lbrace;
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) &lbrace;
        total_count
        items &lbrace;
          name
          sku
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>
1. Compruebe la respuesta.

<u>Resultados esperados</u>:

La lista de productos en la respuesta de GraphQL debe cambiarse según el criterio de ordenación.

<u>Resultados reales</u>:

El criterio de ordenación permanece sin cambios.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en nuestra documentación para desarrolladores.
