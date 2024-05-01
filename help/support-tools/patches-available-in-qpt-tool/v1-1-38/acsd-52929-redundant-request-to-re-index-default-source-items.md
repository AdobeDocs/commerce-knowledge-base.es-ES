---
title: "ACSD-52929: Solicitud redundante para reindexar elementos de origen predeterminados"
description: Aplique el parche ACSD-52929 para corregir el problema de Adobe Commerce en el que hay una solicitud redundante para reindexar los elementos de origen predeterminados cuando el indexador de inventario está configurado en modo asincrónico.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929: Solicitud redundante para reindexar elementos de origen predeterminados

El parche ACSD-52929 corrige el problema en el que hay una redundancia de solicitudes para reindexar elementos de origen predeterminados cuando el indexador de inventario está configurado en modo asincrónico. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.38 está instalado. El ID del parche es ACSD-52929. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Hay una redundancia de solicitudes para reindexar los elementos de origen predeterminados cuando el indexador de inventario está configurado en modo asincrónico.

<u>Pasos a seguir</u>:

1. Configurar [!DNL RabbitMQ].
1. Habilite la estrategia de reindexación asíncrona yendo a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** y establecer **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Crear un origen de inventario personalizado.
1. Inicie sesión en [!DNL RabbitMQ] y vaya a la pestaña colas.
1. Marque `inventory.indexer.sourceItem` y asegúrese de que no contenga mensajes.
1. Abra un producto simple desde el servidor y añada *[!UICONTROL stock only]* a la fuente personalizada y guarde el producto.
1. Cargue el `inventory.indexer.sourceItem` cola en la [!DNL RabbitMQ] y, a continuación, compruebe los mensajes.

<u>Resultados esperados</u>:

Solo hay un mensaje en la cola para el origen personalizado.

<u>Resultados reales</u>:

Se muestran dos mensajes en la cola: uno para el origen predeterminado y otro para el origen personalizado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
