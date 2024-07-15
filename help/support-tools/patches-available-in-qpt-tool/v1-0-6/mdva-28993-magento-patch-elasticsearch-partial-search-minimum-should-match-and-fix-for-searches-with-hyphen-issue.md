---
title: '''MDVA-28993: búsqueda parcial del Elasticsearch, "el mínimo debe coincidir" y corregir el problema de "búsquedas con guiones"'
description: El parche MDVA-28993 implementa la funcionalidad "Mínimo debe coincidir" y la búsqueda parcial del motor de Elasticsearch, y resuelve problemas con guiones en las consultas de búsqueda. El parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6.
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993: Búsqueda parcial del Elasticsearch, &quot;el mínimo debe coincidir&quot; y corrección del problema &quot;búsquedas con guion&quot;

El parche MDVA-28993 implementa la funcionalidad &quot;Mínimo debe coincidir&quot; y la búsqueda parcial del motor de Elasticsearch, y resuelve problemas con guiones en las consultas de búsqueda. El parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.3.4

**Compatible con versiones de Adobe Commerce:** Adobe Commerce local/ Adobe Commerce en infraestructura en la nube 2.3.4-2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.


## Problema

Cuando se usa el Elasticsearch 6 para buscar SKU que contiene un guión (-), la búsqueda devuelve demasiados resultados.

<u>Pasos a seguir:</u>

1. Ve a la tienda.

1. En la barra de búsqueda, introduzca una cadena que contenga un guión, por ejemplo &quot;WS-M-Blue&quot;.

<u>Resultado esperado:</u>

Devuelve solo WS-M-Blue.

<u>Resultado real:</u>

Devuelve todos los SKU que empiezan por &quot;WS&quot;.

## Detalles del parche

El parche MDVA-28993 contiene las siguientes correcciones y mejoras:

* implementa la nueva funcionalidad &quot;El mínimo debe coincidir&quot; y la búsqueda parcial del motor de Elasticsearch. Para obtener detalles de configuración, consulte [Configuración de la búsqueda en el catálogo](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match) en nuestra guía del usuario.
* búsqueda parcial de Elasticsearch
* corrige el problema &quot;búsquedas con guiones&quot; descrito anteriormente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
