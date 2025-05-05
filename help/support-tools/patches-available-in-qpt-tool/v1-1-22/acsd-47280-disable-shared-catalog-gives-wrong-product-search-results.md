---
title: '[!DNL ACSD-47280]: deshabilitar el catálogo compartido proporciona resultados de búsqueda de productos incorrectos'
description: Aplique el  [!DNL ACSD-47280] parche para corregir la visualización de los resultados de búsqueda correctos cuando la función de catálogo compartido esté deshabilitada.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: al deshabilitar el catálogo compartido se obtienen resultados de búsqueda de productos incorrectos

La revisión [!DNL ACSD-47280] corrige la visualización de los resultados de búsqueda correctos cuando la característica [!DNL shared catalog] está deshabilitada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22. [!DNL patch ID] es [!DNL ACSD-47280]. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Use [!DNL patch ID] como palabra clave de búsqueda para localizar el parche.

## Problema

Al deshabilitar [!DNL shared catalog] se obtienen resultados de búsqueda de productos incorrectos.

<u>Requisitos previos</u>:

* [!DNL B2B] módulos instalados

<u>Pasos a seguir</u>:

1. Cree un segundo sitio web.
1. Asigne un producto al segundo sitio web.
1. Comprobar productos en **segundo sitio web** con [!DNL GraphQL]:

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

1. Habilitar **[!UICONTROL Shared Catalog]** en [!DNL scope] predeterminado.
1. La solicitud [!DNL GraphQL] ya no muestra ningún producto para el segundo sitio web, que es el resultado correcto.
1. Vaya al [!DNL scope] del segundo sitio web y deshabilite **[!UICONTROL Company]**.

<u>Resultados esperados</u>:

La solicitud [!DNL GraphQL] aún debe mostrar productos para el segundo sitio web.

<u>Resultados reales</u>:

La solicitud [!DNL GraphQL] no muestra ningún producto para el segundo sitio web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
