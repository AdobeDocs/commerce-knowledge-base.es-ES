---
title: '"MDVA-43983: Los productos configurados como "No visible individualmente" aparecen en los resultados de búsqueda"'
description: El parche MDVA-43983 soluciona el problema de que los productos configurados como "No visibles individualmente" siguen apareciendo en los resultados de búsqueda avanzada del catálogo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. El ID del parche es MDVA-43983. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983: Los productos configurados como &quot;No visible individualmente&quot; aparecen en los resultados de búsqueda

El parche MDVA-43983 soluciona el problema de que los productos configurados como &quot;No visibles individualmente&quot; siguen apareciendo en los resultados de búsqueda avanzada del catálogo. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. El ID del parche es MDVA-43983. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos que se establecen como &quot;No visible individualmente&quot; siguen apareciendo en los resultados de búsqueda avanzada del catálogo.

<u>Pasos a seguir</u>:

1. Cree un atributo con **Tipo de entrada de catálogo para el propietario de la tienda** como **Menú desplegable** o **Muestra visual** (por ejemplo, Color).
1. Establezca **Usar en la búsqueda** como **Sí** y **Visible en la búsqueda avanzada** como **Sí**.
1. Añada algunas opciones de atributos.
1. Cree productos con **Visibilidad** como **No visible de forma individual**.
1. Asignar opciones de atributo de color.
1. Vaya a la página **Búsqueda avanzada en el catálogo** de la tienda.
1. Seleccione únicamente la opción Atributo de color en el campo Atributo de color y deje el resto de los campos en blanco o tal cual.
1. Envíe un formulario de búsqueda avanzada.
1. Observe los resultados de la búsqueda.

<u>Resultados esperados</u>:

Los productos que se establecen como &quot;No visibles individualmente&quot; no aparecen en los resultados de búsqueda avanzada del catálogo.

<u>Resultados reales</u>:

Los productos que se establecen como &quot;No visibles individualmente&quot; aparecen en los resultados de búsqueda avanzada del catálogo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
