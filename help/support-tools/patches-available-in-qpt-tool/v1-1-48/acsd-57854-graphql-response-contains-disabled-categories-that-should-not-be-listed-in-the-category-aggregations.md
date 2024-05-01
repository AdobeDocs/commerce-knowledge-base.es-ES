---
title: "ACSD-57854: la respuesta *GraphQL* contiene categorías deshabilitadas que no deben enumerarse en las agregaciones de categorías"
description: Aplique el parche ACSD-57854 para solucionar el problema de Adobe Commerce donde la respuesta *GraphQL* contiene categorías desactivadas que no deberían aparecer en las agregaciones de categorías.
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854: *GraphQL* la respuesta contiene categorías deshabilitadas que no deben enumerarse en las agregaciones de categorías

El parche ACSD-57854 corrige el problema en el que la variable *GraphQL* La respuesta de contiene categorías deshabilitadas que no deberían enumerarse en las agregaciones de categorías. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.48 está instalado. El ID del parche es ACSD-57854. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

*GraphQL* La respuesta de contiene categorías deshabilitadas que no deberían enumerarse en las agregaciones de categorías.

<u>Pasos a seguir</u>:

1. Cree dos categorías.
1. Cree un producto (Producto de Adobe de prueba) y asígnelo a ambas categorías.
1. Deshabilite una de las categorías que se han creado.
1. Uso de productos *GraphQL* para buscar el producto.
1. Compruebe la lista de categorías de productos en la *GraphQL* respuesta.

<u>Resultados esperados</u>:

Las categorías deshabilitadas no aparecen en la lista *GraphQL* respuesta.

<u>Resultados reales</u>:

Las categorías deshabilitadas se enumeran en la agregación de categorías *GraphQL* respuesta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
