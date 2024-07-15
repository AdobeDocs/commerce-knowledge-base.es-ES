---
title: "MDVA-22383: los indexadores de reglas de destino tardan en indexar"
description: El parche MDVA-22383 resuelve el problema de que la reindexación de los indexadores de producto/regla de destino y regla de destino/producto está tardando demasiado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MDVA-22383. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.5.
exl-id: fbf28983-5883-4769-90bd-1c97c2b2e2b8
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-22383: los indexadores de reglas de destino tardan en indexar

El parche MDVA-22383 resuelve el problema de que la reindexación de los indexadores de producto/regla de destino y regla de destino/producto está tardando demasiado. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MDVA-22383. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.3.2

**Compatible con versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0-2.3.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La reindexación de la regla de producto/destino y de los indexadores de producto/regla de destino está tardando demasiado.

<u>Requisitos previos:</u> el problema ocurre cuando hay un gran número de productos.

<u>Pasos a seguir:</u>

1. Cree una regla de Target con productos para que coincidan con las condiciones. Las condiciones deben agregar más productos a la colección y deben tener atributos (no categorías ni conjuntos de atributos).
1. Ejecute el siguiente comando:

   ```bash
       bin/magento indexer:reindex targetrule_product_rule
   ```

<u>Resultado real:</u>

La reindexación está atascada; el ahorro de productos está atascado.

<u>Resultado esperado:</u>

La reindexación se ha completado correctamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
