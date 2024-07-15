---
title: 'MDVA-43601: los Déclencheur se eliminan de la tabla "catalog_product_price" después de la reindexación completa'
description: El parche MDVA-43601 corrige el problema en el que los déclencheur se eliminan de la tabla "catalog_product_price" después de un reíndice completo de "catalog_rule" o "catalog_product". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. El ID del parche es MDVA-43601. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: los Déclencheur se eliminan de la tabla &quot;catalog_product_price&quot; después de la reindexación completa

La revisión MDVA-43601 corrige el problema en el cual los déclencheur se eliminan de la tabla `catalogrule_product_price` después de un reíndice completo de `catalogrule_rule` o `catalogrule_product`. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. El ID del parche es MDVA-43601. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los déclencheur se quitan de la tabla `catalogrule_product_price` después de un reíndice completo de `catalogrule_rule` o `catalogrule_product`.

<u>Pasos a seguir</u>:

1. Establecer todos los indizadores en *Actualizar por programación*.
1. Compruebe las déclencheur creadas para la tabla `catalogrule_product_price` ejecutando la siguiente solicitud SQL:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Reindexe manualmente `catalogrule_rule` o `catalogrule_product` ejecutando el siguiente comando: `bin/magento indexer:reindex catalogrule_rule`
1. Vuelva a comprobar los déclencheur de la tabla `catalogrule_product_price`.

<u>Resultados esperados</u>:

Los déclencheur de la tabla `catalogrule_product_price` se conservan después de un reíndice completo.

<u>Resultados reales</u>:

No se encontraron déclencheur para la tabla `catalogrule_product_price`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
