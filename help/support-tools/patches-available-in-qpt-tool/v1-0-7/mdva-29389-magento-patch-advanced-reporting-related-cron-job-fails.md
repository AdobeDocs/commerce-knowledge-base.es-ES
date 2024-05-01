---
title: "MDVA-29389: El trabajo cron relacionado con los informes avanzados falla"
description: '"El parche de MDVA-29389 corrige el problema de los informes avanzados, donde el cronjob "analytics_collect_data" dice: "*Port debe configurarse dentro del parámetro del host (como localhost:3306)*". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. El ID del parche es MDVA-29389. El problema se solucionó en Adobe Commerce 2.4.2."'
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389: el trabajo cron relacionado con los informes avanzados falla

El parche de MDVA-29389 soluciona el problema de los informes avanzados en los que la variable `analytics_collect_data` cronjob dice: &quot;*El puerto debe configurarse en el parámetro host (como localhost:3306)*&quot;. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalado. El ID del parche es MDVA-29389. El problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4.

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. En la instancia de Adobe Commerce, habilite Informes avanzados.
1. Ejecute la siguiente consulta para insertar el valor analytics/general/token en la base de datos:

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. Abra env.php y agregue el puerto al parámetro de host en la configuración de la base de datos con el siguiente formato: `'host' => 'hostname:port',`
1. Borrar caché.
1. Ejecute el `analytics_collect_data` trabajo cron.

<u>Resultados esperados</u>:

El `analytics_collect_data` El trabajo se ejecuta correctamente cuando se utiliza el puerto predeterminado o no predeterminado para conectarse a MySQL en env.php.

<u>Resultados reales</u>:

El `analytics_collect_data` el trabajo genera un error &quot;*El puerto debe configurarse en el parámetro host (como localhost:3306)*&quot; cuando se usa un puerto no predeterminado para conectarse a MySQL en env.php.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
