---
title: "MDVA-44505: La consulta de GraphQL para el carro de compras que aplica puntos de recompensa no actualiza el total general"
description: El parche MDVA-44505 resuelve el problema en el que la consulta de GraphQL para un carro de compras que aplica puntos de recompensa no considera los puntos de recompensa y devuelve un total general incorrecto. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. El ID del parche es MDVA-44505. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: 724273ba-b020-4dba-88ae-94968bbd83de
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44505: La consulta de GraphQL para el carro de compras que aplica puntos de recompensa no actualiza el total general

El parche MDVA-44505 resuelve el problema en el que la consulta de GraphQL para un carro de compras que aplica puntos de recompensa no considera los puntos de recompensa y devuelve un total general incorrecto. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 está instalado. El ID del parche es MDVA-44505. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta de GraphQL para un carro de compras que aplica puntos de recompensa no tiene en cuenta los puntos de recompensa y devuelve un total general incorrecto.

<u>Pasos a seguir</u>:

1. Configure los puntos de recompensa.
1. Crear un carro de compras y aplicar algunos puntos de recompensa.
1. Llame a `GetCart` consulta desde el `GraphQL` y recupere el carro de compras:

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Compruebe la entrada del total general.
1. Ahora compruebe el total del carro de compras del cliente mediante la API de REST (`/rest/V1/carts/mine/totals`).

<u>Resultados esperados</u>:

La consulta de GraphQL para el carro de compras devuelve el total general correcto que tiene en cuenta los puntos de recompensa.

<u>Resultados reales</u>:

La consulta de GraphQL no tiene en cuenta los puntos de recompensa y devuelve un total general incorrecto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
