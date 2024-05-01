---
title: "Parche de MDVA-30284: Elasticsearch 7: se ha superado el límite de campos totales [XXXXX] en el índice"
description: El parche de MDVA-30284 soluciona el problema en el que se recibe un mensaje de error que indica que "Se ha superado el límite de campos totales \[XXXXX\] en el índice" al utilizar el Elasticsearch 7. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5. El ID del parche es MDVA-30284.
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Parche de MDVA-30284: Elasticsearch 7: límite de campos totales [XXXXX] se ha superado el índice

El parche de MDVA-30284 soluciona el problema en el que se recibe un mensaje de error que indica que &quot;Se ha superado el límite de campos totales \[XXXXX\] en el índice&quot; al utilizar el Elasticsearch 7. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 está instalado. El ID del parche es MDVA-30284.

## Productos y versiones afectados

* El parche se ha diseñado para Adobe Commerce en la infraestructura en la nube 2.3.5-p2
* Elasticsearch 7 es compatible con Adobe Commerce 2.3.5 y 2.4.x

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El límite de campos de Elasticsearch es incorrecto, lo que provoca el siguiente error al ejecutar el indexador \[catalogsearch\_fulltext\]:

*Límite de campos totales [xxx] en el índice [xxxxxx] se ha excedido*

Este problema se produce cuando tiene un gran número de atributos de producto. El problema se activa por la forma en que el Elasticsearch calcula el recuento de campos. A veces, cuando hay atributos que tienen campos asignados, estos campos se indexan como indexadores independientes. Esto hace que se haya superado el límite de advertencia.

<u>Pasos a seguir:</u>

<u>Requisitos previos</u>

* Se ha instalado module-elasticsearch 100.3.5.
* Elasticsearch 7 instalado.
* Configure el Elasticsearch como backend de búsqueda.

1. Cree más de 1000 atributos para los productos.
1. Cree productos para cada familia.
1. Ejecute el indexador.

<u>Resultado esperado:</u>

Todos los productos están disponibles en el índice de Elasticsearch.

<u>Resultado real:</u>

1. Error del Elasticsearch:

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. El nuevo producto no se ha indexado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
