---
title: "Parche de MCP-87 Adobe Commerce: tienda rota"
description: El parche de MCP-87 Adobe Commerce ha corregido el problema que causaba que la reindexación de catálogos fuera lenta. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13.
exl-id: 048b2764-6bbf-4a02-9a0a-dbea4e48f92a
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Parche de MCP-87 Adobe Commerce: tienda rota

El parche de MCP-87 Adobe Commerce ha corregido el problema que causaba que la reindexación de catálogos fuera lenta. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en la infraestructura en la nube 2.4.0.

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.1 - 2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La reindexación de stock de catálogos con perfiles grandes es muy lenta.

<u>Pasos a seguir:</u>

1. Inicie sesión en el panel de administración.
1. Vaya a **Productos** > **Catálogo**.
1. Seleccione todos los elementos de la cuadrícula Productos.
1. Seleccione **Actualizar atributos** en la lista desplegable Seleccionar acciones de producto. Haga clic en **Enviar**.
1. Haga clic en **Inventario avanzado** en la ficha Configuración avanzada. Cambiar **disponibilidad de existencias** a *en existencias*. Haga clic en **Guardar**.
1. Realice la reindexación completa manualmente, ejecute el siguiente comando desde la raíz: `bin/magento indexer:reindex`

<u>Resultado esperado:</u>

El indexador de stock reindexa rápidamente.

<u>Resultado real:</u>

El indexador de cotizaciones es muy lento y/o no se completa.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
