---
title: "BB2B-2598: agrega capacidad de almacenamiento en caché a storeConfig, currency, country, countries, availableStores y consultas de GraphQl"
description: Aplique el parche BB2B-2598 para añadir la capacidad de almacenamiento en caché a las consultas storeConfig, currency, country, countries y availableStores de GraphQl.
exl-id: 37551954-d721-4f3a-b237-cd795f715a5f
feature: B2B, GraphQL, Cache
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# BB2B-2598: Añade capacidad de almacenamiento en caché a `storeConfig`, `currency`, `country`, `countries`, y `availableStores` Consultas de GraphQl

El parche BB2B-2598 añade capacidad de almacenamiento en caché a `storeConfig`, `currency`, `country`, `countries`, y `availableStores` Consultas de GraphQL. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 está instalado. El ID del parche es BB2B-2598. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7-beta1.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

`availableStores`, `countries`, `country`, `currency`, `storeConfig`, y `customAttributeMetadata` Las consultas de GraphQL no se pueden almacenar en caché.

<u>Requisitos previos</u>:

* El servidor señala a [!DNL Varnish] proxy al servidor de Adobe Commerce.
* Ajuste de configuración `system/full_page_cache/caching_application` se establece en *2* ([!DNL Varnish]) o vaya a Administración de Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > y configúrelo en [!DNL Varnish].

Una vez aplicado el parche, ejecute los siguientes pasos para asegurarse de que la capacidad de almacenamiento en caché ya esté disponible:

1. Enviar `GET` a cualquiera de las consultas de GraphQL enumeradas anteriormente, utilizando cualquier campo arbitrario.
1. Vuelva a enviar la solicitud sin ningún cambio; notará que es mucho más rápido. Tenga en cuenta que la solicitud no se envía al servidor, pero la gestiona completamente [!DNL Varnish] como una visita de caché.
1. Si se requieren más pruebas, comente la anulación de `X-Magento-Debug` encabezado presente en nuestro [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227), luego reiniciar [!DNL Varnish] y ejecute de nuevo los pasos anteriores.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
