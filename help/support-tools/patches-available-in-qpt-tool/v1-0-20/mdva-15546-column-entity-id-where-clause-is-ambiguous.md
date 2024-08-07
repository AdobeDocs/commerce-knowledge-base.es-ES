---
title: "MDVA-15546: Columna 'entity_id' donde la cláusula es ambigua"
description: '"El parche MDVA-15546 resuelve los problemas de rendimiento que pueden estar relacionados con algunas extensiones de Amazon. Este problema se indica con el siguiente error en los registros de excepciones: *donde*   *Columna ''entity\\_id'' en la que la cláusula es ambigua, la consulta era: SELECT \\`main\\_table\`.\\*, \\`extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\`. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MDVA-15546".'
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546: Columna &#39;entity_id&#39; donde la cláusula es ambigua

El parche MDVA-15546 resuelve los problemas de rendimiento que pueden estar relacionados con algunas extensiones de Amazon. Este problema se indica mediante el siguiente error en los registros de excepciones: *donde*   *Columna &#39;entity\_id&#39; en la que la cláusula es ambigua, la consulta era: SELECT \`main\_table\`.\*, \`extension\_attribute\_amazon\_order\_reference\_id* \`. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MDVA-15546.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.2.5

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.0 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Problemas de rendimiento que pueden estar relacionados con algunas extensiones de Amazon.

<u>Requisitos previos</u>:

Limpie Adobe Commerce con B2B y Amazon\_Payment.

<u>Pasos a seguir</u>:

1. Vaya a la página de la tienda.
1. Añadir producto al carro de compras.
1. Espere o déclencheur el trabajo cron `flush_preview_quotas`.

<u>Resultado real</u>:

Cuando marque `var/log/exception/log`, verá el siguiente error:

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `tabla_principal`.*, `atributo_de_extensión_amazon_order_reference_id`.`id_de_referencia_orden_amazonas` AS `atributo_de_extensión_amazon_order_reference_id_referencia_orden_amazonas`, `atributo_de_extensión_amazon_order_reference_id`.`quote_id` AS `atributo_de_extensión_amazon_order_reference_id_cita`, `atributo_de_extensión_amazon_order_reference_id`.` simulation_reference` AS `atributo_de_extensión_amazon_order_reference_sandbox simulation_reference`, `extension_attribute_amazon_order_reference_id`.`confirmado` AS `extension_attribute_amazon_order_reference_id_confirm` FROM `quote` AS `tabla_principal` LEFT JOIN `amazon_quote` AS `extension_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*

<u>Resultado esperado</u>:

El trabajo de cron se completa sin errores.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
