---
title: '"ACSD-51857: El trabajo cron lento de "aggregate_sales_report_bestsellers_data" afecta al rendimiento"'
description: Aplique el parche ACSD-51857 para corregir el problema de Adobe Commerce en el que el trabajo cron lento `aggregate_sales_report_bestsellers_data` afecta a grandes tablas de base de datos "sales_order" y "sales_order_item".
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: trabajo cron lento de `aggregate_sales_report_bestsellers_data` afecta al rendimiento

El parche ACSD-51857 corrige el problema en el que el trabajo cron lento `aggregate_sales_report_bestsellers_data` afecta a grandes `sales_order` y `sales_order_item` tablas de base de datos. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 está instalado. El ID del parche es ACSD-51857. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Rendimiento del trabajo cron de `aggregate_sales_report_bestsellers_data` es lento en `sales_order` y `sales_order_item` tablas de base de datos.

Para resolver esto, se ha vuelto a escribir la consulta de datos principal que captura los datos del informe en un formulario más eficiente. Ahora se utiliza una subconsulta para determinar el subconjunto de datos.

Para que la subconsulta funcionara lo más rápido posible, se agregó un nuevo índice para `sales_order` tabla de base de datos: `SALES_ORDER_STORE_STATE_CREATED` basado en `store_id`, `state`, y `created_at` columnas.

<u>Requisitos previos</u>

Asegúrese de un gran número de pedidos diarios.

<u>Pasos a seguir</u>

1. Ejecute el `aggregate_sales_report_bestsellers_data` trabajo cron.
1. Compruebe los datos que se van a mostrar en el panel de administración, en la **[!UICONTROL Bestsellers]** pestaña.

<u>Resultados esperados</u>:

*[!UICONTROL Quantity per source]* en el **[!UICONTROL Configuration]** La pestaña no debe estar vacía.

<u>Resultados reales</u>:

*[!UICONTROL Quantity per source]* en el **[!UICONTROL Configuration]** está vacía.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
