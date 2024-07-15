---
title: "MDVA-34189: El comerciante visual ejecuta consultas MySQL"
description: El parche MDVA-34189 soluciona el problema en el que Adobe Commerce ejecuta consultas grandes de Visual Merchandiser al cargar la página de categoría de Administración.
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189: El comerciante visual ejecuta consultas MySQL largas

El parche MDVA-34189 soluciona el problema en el que Adobe Commerce ejecuta consultas grandes de Visual Merchandiser al cargar la página de categoría de Administración.

Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. El ID del parche es MDVA-34189. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.3.5-p2

**Compatible con versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.4-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El sitio web ejecuta consultas MySQL grandes en el servidor de producción.

<u>Pasos a seguir</u>:

1. Para acceder a Visual Merchandiser, ve a la barra lateral de *Admin* y haz clic en **Catálogo** > **Categorías**.
1. Cargue la página **Categorías** en el panel de administración (la carga inicial de la categoría raíz) y observe las consultas que ejecuta.

<u>Resultado esperado</u>:

La página Administrador **Categorías** debe cargarse sin generar consultas lentas.

<u>Resultado real</u>:

Esto depende de la configuración de PHP. El ejemplo más común de este error es que la página **Categorías** no se abre y se muestra un error *Error 503 de tiempo de espera de primer byte*.

Como alternativa, cuando Adobe Commerce carga Visual Merchandiser, ejecuta una consulta MySQL lenta. Esta consulta incluye muchos ID de producto insertados en `ORDER BY FIELD(`e`.`entity_id`,  ...)`

en `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
