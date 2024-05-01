---
title: "ACSD-47332: cron falla con un error notificado solo entre las 00:00 y las 00:59 UTC"
description: Aplique el parche ACSD-47332 para corregir el problema de Adobe Commerce en el que cron falla con un error que se registra solo cuando se ejecuta entre 00:00 y 00:59 UTC.
exl-id: a4eac977-6d0a-4e36-8576-68777c1e40b2
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47332: cron falla con un error notificado solo cuando se ejecuta entre 00:00 y 00:59 UTC

El parche ACSD-47332 corrige el problema en el que cron falla con un error que se comunica solo cuando se ejecuta entre 00:00 y 00:59 UTC. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 está instalado. El ID del parche es ACSD-47332. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cron falla con un error que se informa solo cuando se ejecuta entre las 00:00 y las 00:59 UTC.

<u>Pasos a seguir</u>:

1. Ejecute el `catalog_index_refresh_price` CRON entre 00:00 y 00:59 UTC.

<u>Resultados esperados</u>:

Cron no muestra errores.

<u>Resultados reales</u>:

Cron falla con el siguiente error.

```SQL
SQLSTATE[HY093]: Invalid parameter number: number of bound variables does not match number of tokens, query was: SELECT `cat`.`entity_id` FROM `c
  atalog_product_entity_datetime` AS `attr`
   LEFT JOIN `catalog_product_entity` AS `cat` ON cat.row_id= attr.row_id AND (cat.created_in <= 1 AND cat.updated_in > 1) WHERE (attr.attribute_id
   = '79') AND (attr.store_id = '0') AND (attr.value = DATE_FORMAT('2022-10-02', '%Y-%m-%d %H:%i:%s'))
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
