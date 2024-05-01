---
title: 'MDVA-37182: resultados de búsqueda incoherentes en el Elasticsearch 6 y 7'
description: El parche MDVA-37182 corrige el problema con un comportamiento de búsqueda incoherente en las versiones 6 y 7 de Elasticsearch. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. El ID del parche es MDVA-37182. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182: resultados de búsqueda incoherentes en Elasticsearch 6 y 7

El parche MDVA-37182 corrige el problema con un comportamiento de búsqueda incoherente en las versiones 6 y 7 de Elasticsearch. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 está instalado. El ID del parche es MDVA-37182. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.1-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Comportamiento de búsqueda incoherente.

<u>Pasos a seguir</u>:

1. Cree productos con los siguientes detalles:
   * Nombres: &quot;5127AC&quot;, &quot;5127SS&quot;, &quot;5127AB&quot;
   * SKU: &quot;product1&quot;, &quot;product2&quot;, &quot;product3&quot;
1. Configure el motor de búsqueda en el Elasticsearch 6 (ES6).
1. Ejecutar reindexación completa.
1. En la tienda, busca &quot;5127s&quot;.
1. Configure el motor de búsqueda en el Elasticsearch 7 (ES7).
1. Ejecutar reindexación completa.
1. En la tienda, busca &quot;5127s&quot;.

<u>Resultado real:</u>:

ES6: la búsqueda no devuelve resultados.ES7: la búsqueda devuelve tres productos.

<u>Resultado esperado:</u>:

La búsqueda devuelve un producto para ambas versiones.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
