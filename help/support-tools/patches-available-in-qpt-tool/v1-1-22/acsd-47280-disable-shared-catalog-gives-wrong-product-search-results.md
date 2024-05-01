---
title: '''[!DNL ACSD-47280]: Deshabilitar el catálogo compartido proporciona resultados de búsqueda de productos incorrectos'
description: Aplique la variable [!DNL ACSD-47280] parche para corregir la visualización de los resultados de búsqueda correctos cuando la función de catálogo compartido está desactivada.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: al deshabilitar el catálogo compartido, se obtienen resultados de búsqueda de productos incorrectos

El [!DNL ACSD-47280] parche corrige la visualización de los resultados de búsqueda correctos cuando la variable [!DNL shared catalog] Esta función está desactivada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 está instalado. El [!DNL patch ID] es [!DNL ACSD-47280]. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el [!DNL patch ID] como palabra clave de búsqueda para localizar el parche.

## Problema

Desactivando [!DNL shared catalog] da resultados de búsqueda de productos incorrectos.

<u>Requisitos previos</u>:

* [!DNL B2B] módulos instalados

<u>Pasos a seguir</u>:

1. Cree un segundo sitio web.
1. Asigne un producto al segundo sitio web.
1. Compruebe los productos en la **segundo sitio web** usando [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Activar **[!UICONTROL Shared Catalog]** de forma predeterminada [!DNL scope].
1. El [!DNL GraphQL] La solicitud ya no muestra ningún producto para el segundo sitio web, lo cual es el resultado correcto.
1. Vaya a la [!DNL scope] de la segunda página web y deshabilitar **[!UICONTROL Company]**.

<u>Resultados esperados</u>:

El [!DNL GraphQL] la solicitud aún debe mostrar los productos del segundo sitio web.

<u>Resultados reales</u>:

El [!DNL GraphQL] La solicitud no muestra ningún producto para el segundo sitio web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
