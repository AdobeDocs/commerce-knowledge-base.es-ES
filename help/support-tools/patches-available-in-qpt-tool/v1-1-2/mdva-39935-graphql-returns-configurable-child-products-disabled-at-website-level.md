---
title: "MDVA-39935: GraphQL devuelve productos secundarios configurables desactivados en el nivel de sitio web"
description: El parche de MDVA-39935 Adobe Commerce corrige el problema en el que GraphQL devuelve productos secundarios configurables desactivados en el nivel de sitio web. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2. El ID del parche es MDVA-39935. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 45bd6bd9-3572-4477-a689-d6b952a3290a
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39935: GraphQL devuelve productos secundarios configurables desactivados en el nivel de sitio web

El parche de MDVA-39935 Adobe Commerce corrige el problema en el que GraphQL devuelve productos secundarios configurables desactivados en el nivel de sitio web. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 está instalado. El ID del parche es MDVA-39935. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

GraphQL devuelve productos secundarios configurables incluso después de que estén desactivados en el nivel de sitio web.

<u>Pasos a seguir</u>:

1. Active la opción de visualización de productos sin existencias en **Almacenar** > **Configuración** > **Catálogo** > **Inventario** > **Opciones de Stock** > **Mostrar productos sin existencias** > **Sí**.
1. Seleccionar cualquiera **Producto configurable** que tiene más de dos **Productos simples**.
1. Deshabilitar **Producto sencillo** y guarde el **Producto configurable**.
1. Recupere el **Producto configurable** datos con GraphQL.

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>Resultados esperados</u>:

Los productos desactivados NO se muestran en los resultados de la variante.

<u>Resultados reales</u>:

Los datos de productos desactivados se recuperan en los resultados de la variante.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre parches de calidad para Adobe Commerce, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
