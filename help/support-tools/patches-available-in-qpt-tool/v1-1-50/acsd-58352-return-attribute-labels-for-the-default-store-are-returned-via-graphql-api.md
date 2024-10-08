---
title: 'ACSD-58352: las etiquetas de atributo devueltas para el almacén predeterminado se devuelven mediante [!DNL GraphQL] API'
description: Aplique el parche ACSD-58352 para solucionar el problema de Adobe Commerce donde las etiquetas de atributos de devolución para el almacén predeterminado se devuelven mediante la API  [!DNL GraphQL]  cuando se especifica una vista de almacén no predeterminada en el encabezado de la solicitud.
feature: GraphQL, Returns
role: Admin, Developer
source-git-commit: 6df1ec7e2cccfbadaa88b8233ca99faf40a208c5
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# ACSD-58352: las etiquetas de atributo devueltas para el almacén predeterminado se devuelven mediante la API [!DNL GraphQL]

La revisión ACSD-58352 corrige el problema en el que las etiquetas de atributos de retorno para el almacén predeterminado se devuelven mediante la API [!DNL GraphQL] cuando se especifica una vista de almacén no predeterminada en el encabezado de la solicitud. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. El ID del parche es ACSD-58352. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las etiquetas de atributo devueltas para la tienda predeterminada se devuelven mediante la API [!DNL GraphQL].

<u>Pasos a seguir</u>:

1. Habilite **[!UICONTROL Return Merchandising Authorization]**.
1. Crear un *[!UICONTROL Additional Store]* y un *[!UICONTROL Store View]* en el sitio web predeterminado.
1. Edite el atributo de retorno **[!UICONTROL Reason for Return]** y agregue etiquetas para todas las vistas de tiendas.
1. Crear un *[!UICONTROL Order]*.
1. Cree un(a) *[!UICONTROL Return]* para ese pedido. Asegúrese de que *[!UICONTROL Return]* se encuentre en el estado *[!UICONTROL Pending]*.
1. Enviar una consulta de cliente [!DNL GraphQL] con el valor especificado no predeterminado [!UICONTROL Store View] en el encabezado:

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Observe la respuesta.

<u>Resultados esperados</u>

Las etiquetas de devolución de la respuesta [!DNL GraphQL] son para [!UICONTROL Store View] establecido en el encabezado de la solicitud.

<u>Resultados reales</u>:

Las etiquetas devueltas en la respuesta [!DNL GraphQL] son para el valor predeterminado [!UICONTROL Store View].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].