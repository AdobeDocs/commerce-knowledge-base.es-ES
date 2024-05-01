---
title: "ACSD-54324: La solicitud de GraphQL request_lists no tiene en cuenta la configuración de paginación"
description: Aplique el parche ACSD-54324 para solucionar el problema de Adobe Commerce en el que la solicitud de GraphQL "request_lists" no tiene en cuenta la configuración de paginación y devuelve todos los resultados.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` la solicitud no tiene en cuenta la configuración de paginación

El parche ACSD-54324 corrige el problema en el que la GraphQL `requisition_lists` la solicitud no tiene en cuenta la configuración de paginación y devuelve todos los resultados. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.41 está instalado. El ID del parche es ACSD-54324. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El GraphQL `requisition_lists` la solicitud no tiene en cuenta la configuración de paginación y devuelve todos los resultados.

<u>Pasos a seguir</u>:

1. Inicie sesión en Admin y navegue hasta **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Establecer *[!UICONTROL Enable Requisition List]* hasta *Sí*.

1. Inicie sesión en el front-end de y vaya a **[!UICONTROL My Requisition Lists]** desde el menú superior o desde **[!UICONTROL My Account]** y cree varias solicitudes (por ejemplo, 7).
1. Después de generar un token de cliente, ejecute el siguiente GraphQL `requisition_lists` consulta para el cliente.

   * Asegúrese de que el tamaño de página es inferior al número total de listas de solicitudes creadas (por ejemplo: 4)

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Observe que el valor de `total_count` el campo muestra 7, cuando debería mostrar 4.

   El número de elementos también indica 7 cuando debería ser el mismo que el *tamaño de página*.

<u>Resultados esperados</u>:

* El número indicado como *tamaño de página* se devuelve en `total_count` y no el número total de registros.
* El número de elementos es el mismo que el *tamaño de página*.

<u>Resultados reales</u>:

El número total de registros se devuelve en `total_count`, incluso si *tamaño de página* se menciona.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
