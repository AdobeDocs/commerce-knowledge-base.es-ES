---
title: "MDVA-40134: GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado"
description: El parche de MDVA-40134 corrige el problema en el que GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-40134. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134: GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado

El parche de MDVA-40134 corrige el problema en el que GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-40134. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado.

<u>Requisitos previos</u>:

Deben instalarse los módulos B2B.
La instancia debe estar limpia con solo los datos de ejemplo.

<u>Pasos a seguir</u>:

1. Vaya a **Tiendas** > **Configuración** > **General** > **Características B2B** y habilite **Compañía y catálogo compartido**.
1. Vaya a **Catálogo** > **Catálogo compartido** y agregue todos los productos al **Catálogo general**.
1. Utilice los datos de ejemplo y modifique la bolsa de lona Joust (SKU 24-MB01).
1. En **Productos relacionados**, agregue las dos bolsas Duffle (ID 7 y 13).
1. Enviar una solicitud **Post**:

<pre>{
  products(filter: {sku: {eq: "24-MB01"}}, sort: {name: ASC}) {
    elementos {
      related_products {
        uid
        name
      }
    }
  }
}</pre>

<u>Resultados esperados</u>:

Los productos relacionados se muestran en la respuesta de GraphQL.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente error:

<pre>El valor devuelto de Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() debe ser del tipo int, null devuelto {"exception":"[object] (GraphQL\\Error\\Error(code: 0): El valor devuelto de Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() debe ser del tipo int, null devuelto </pre>

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
