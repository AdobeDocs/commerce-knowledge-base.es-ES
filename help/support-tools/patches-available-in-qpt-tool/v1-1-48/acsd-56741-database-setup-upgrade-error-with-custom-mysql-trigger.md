---
title: "ACSD-56741: Solución de problemas de configuración de bases de datos con déclencheur MySQL personalizados"
description: Aplique el parche ACSD-56741 para corregir el problema de Adobe Commerce donde aparece un mensaje de error *Intentando acceder al desplazamiento de la matriz en un valor de tipo nulo* durante setup:upgrade debido a un déclencheur MySQL personalizado en la base de datos no relacionado con la indexación y [!DNL MView].
feature: Install
role: Admin, Developer
source-git-commit: 216ce1035584e4c049029073ee0017d3616cdbd6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741: solución de problemas de configuración de bases de datos con déclencheur MySQL personalizados

El parche ACSD-56741 corrige el problema en el que se mostraba un mensaje de error *Intentando obtener acceso al desplazamiento de la matriz en un valor de tipo nulo* aparece durante `setup:upgrade` debido a un déclencheur MySQL personalizado en la base de datos no relacionado con la indexación y [!DNL MView]. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 está instalado. El ID del parche es ACSD-56741. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un mensaje de error *Intentando obtener acceso al desplazamiento de la matriz en un valor de tipo nulo* aparece durante `setup:upgrade` debido a un déclencheur MySQL personalizado en la base de datos no relacionado con la indexación y [!DNL MView].

<u>Pasos a seguir</u>:

1. Ejecutar `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Ejecutar `php bin/magento c:f`.
1. Ejecutar `php bin/magento setup:upgrade`.

<u>Resultados esperados</u>:

La actualización de la instalación finaliza sin ningún error.

<u>Resultados reales</u>:

La actualización de la instalación se cierra con un mensaje de error:

*Advertencia: Intentando acceder al desplazamiento de la matriz en un valor de tipo nulo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
