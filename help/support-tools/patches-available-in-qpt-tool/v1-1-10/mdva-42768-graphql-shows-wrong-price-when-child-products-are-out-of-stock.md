---
title: "MDVA-42768: GraphQL muestra un precio incorrecto cuando los productos secundarios están agotados"
description: El parche MDVA-42768 soluciona el problema de que GraphQL muestra el precio incorrecto cuando los productos secundarios de un producto configurable no están disponibles. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-42768. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 012e7e21-e508-4449-98a6-4bdb41284c3a
feature: GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# MDVA-42768: GraphQL muestra un precio incorrecto cuando los productos secundarios están agotados

El parche MDVA-42768 soluciona el problema de que GraphQL muestra el precio incorrecto cuando los productos secundarios de un producto configurable no están disponibles. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalado. El ID del parche es MDVA-42768. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando los productos secundarios de un producto configurable están agotados y la configuración Mostrar productos sin existencias está activada, la consulta GraphQL muestra el precio normal del producto como **0**.

<u>Requisitos previos</u>:

Se instalan los datos de ejemplo.

<u>Pasos a seguir</u>:

1. Habilite la configuración del producto Mostrar sin existencias en el administrador de Commerce yendo a **Tiendas** > **Configuración** > **Catálogo** > **Inventario**.
1. Cree un producto configurable y asígnele un producto secundario simple.
1. Establezca el inventario del producto de variante (simple) en **Sin existencias**.
1. Reindexe.
1. Ejecute la siguiente consulta de GraphQL:

   ```GraphQL
   query {
     products(filter: { sku: { eq: "MH01" } }) {
       items {
         sku
         price_range {
           minimum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
           maximum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
         }
       }
     }
   }
   ```

1. Compruebe la sección de respuesta `minimum_price` > `regular price`.

<u>Resultados esperados</u>:

El precio mínimo regular no se muestra como 0 en respuesta.

<u>Resultados reales</u>:

El precio mínimo normal = 0 en respuesta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
