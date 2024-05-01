---
title: "ACSD-56090: la respuesta de GraphQL no es específica del almacén"
description: Aplique el parche ACSD-56090 para solucionar el problema de Adobe Commerce, donde la respuesta de GraphQL contiene todos los almacenes de datos en lugar de los específicos del almacén de datos.
feature: GraphQL
role: Admin, Developer
exl-id: 129491e0-1a77-4ccc-8aba-cd0afdb26176
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56090: la respuesta de GraphQL no es específica del almacén

El parche ACSD-56090 corrige el problema en el que la respuesta de GraphQL contiene todos los datos de los almacenes en lugar de los datos específicos de los almacenes. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 está instalado. El ID del parche es ACSD-56090. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La respuesta de GraphQL contiene todos los datos de los almacenes en lugar de los datos específicos del almacén.

<u>Pasos a seguir</u>:

1. Inicie sesión en **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** y cree dos categorías raíz.
1. Cada categoría raíz debe tener una subcategoría.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL All stores]** > Hay dos tiendas con diferentes categorías raíz para cada una. (Cada tienda debe tener al menos una vista de tienda)
1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > crear un producto con

* Todas las categorías raíz y subcategorías asignadas
* Todos los sitios web asignados.

1. Ejecute la consulta de GraphqQL (añadir encabezado — store = &#39;storename ):

```
   query {
     products(filter: { url_key: { eq: "abc" } }) {
       items {
         categories {
           name
           id
           url_path
           breadcrumbs {
             category_id
             category_name
             category_level
           }
         }
       }
     }
   }
```

1. Compruebe la respuesta después de ejecutar la consulta de GraphqQL.

<u>Resultados esperados</u>:

Se devuelven los datos específicos del almacén

<u>Resultados reales</u>:

Los datos devueltos no son específicos del almacén.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
