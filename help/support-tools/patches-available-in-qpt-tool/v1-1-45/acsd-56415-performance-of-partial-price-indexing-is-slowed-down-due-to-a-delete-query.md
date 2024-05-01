---
title: '"ACSD-56415: Rendimiento de [!UICONTROL Partial Price Indexing] ralentizado debido a la consulta "DELETE"'
description: Aplique el parche ACSD-56415 para corregir el problema de Adobe Commerce en el que el rendimiento del [!UICONTROL Partial Price Indexing] se ralentiza debido a una consulta "DELETE" cuando la base de datos tiene muchos datos de precios parciales que indexar.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: rendimiento de [!UICONTROL Partial Price Indexing] se ha ralentizado debido a `DELETE` query

El parche ACSD-56415 corrige el problema en el que el rendimiento del [!UICONTROL Partial Price Indexing] se ralentiza debido a un `DELETE` consulta cuando la base de datos tiene un montón de índice de datos de precios parciales. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 está instalado. El ID del parche es ACSD-56023. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El rendimiento de [!UICONTROL Partial Price Indexing] se ralentiza debido a un `DELETE` consulta cuando la base de datos tiene un montón de índice de datos de precios parciales.

<u>Pasos a seguir</u>:

1. Crear *300000 productos* y *10 sitios web* uso del perfil de rendimiento grande.
1. Inicie sesión en el panel de administración.
1. Crear *10 grupos de clientes*.
1. Ejecute la siguiente consulta para agregar productos a `_cl` tabla:

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Ejecute el siguiente comando para almacenar en déclencheur el proceso de indexación de precios parcial:

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>Resultados esperados</u>:

El DELETE de consultas SQL `main_table` DESDE `catalog_product_index_price` se ejecuta rápidamente.

<u>Resultados reales</u>:

El DELETE de consultas SQL `main_table` DESDE `catalog_product_index_price` se ejecuta muy lentamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
