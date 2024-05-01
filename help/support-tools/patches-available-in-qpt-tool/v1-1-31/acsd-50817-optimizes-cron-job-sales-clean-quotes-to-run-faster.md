---
title: "ACSD-50817: Optimiza el trabajo cron sales_clean_quote para que se ejecute más rápido"
description: Aplique el parche ACSD-50817 para optimizar el trabajo cron "sales_clean_quote" para que se ejecute más rápido añadiendo un índice compuesto en las columnas "store_id" y "updated_at" en la tabla de ofertas.
exl-id: b08b12ff-37ac-4a7d-bce2-2a27e4f916f0
feature: Quotes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-50817: optimiza el trabajo de cron `sales_clean_quotes` para ejecutarse más rápido

El parche ACSD-50817 optimiza el trabajo de cron `sales_clean_quotes` para ejecutarse más rápido añadiendo un índice compuesto en la `store_id` y `updated_at` columnas de la tabla de comillas. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.31 está instalado. El ID del parche es ACSD-50817.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El trabajo cron `sales_clean_quotes` es demasiado lento. Con este parche, se ha optimizado para que se ejecute más rápido añadiendo un índice compuesto en la `store_id` y `updated_at` columnas de la tabla de comillas.

<u>Pasos a seguir</u>:

1. Genere entre 50 y 80 millones de presupuestos con `updated_at` establecer como período &lt; 30 días.
1. Ejecute el trabajo cron `sales_clean_quotes` o la siguiente consulta en la tabla de oferta:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Resultados esperados</u>

Trabajo cron `sales_clean_quotes` está optimizado para ejecutarse más rápido añadiendo un índice compuesto en la `store_id` y `updated_at` columnas de la tabla de comillas.

<u>Resultados reales</u>

La consulta es demasiado lenta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
