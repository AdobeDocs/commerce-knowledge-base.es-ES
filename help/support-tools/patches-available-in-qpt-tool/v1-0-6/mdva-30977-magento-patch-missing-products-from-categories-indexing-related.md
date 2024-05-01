---
title: "MDVA-30977: productos que faltan en las categorías, relacionados con la indexación"
description: El parche MDVA-30977 soluciona los problemas con los productos mostrados en las páginas de categorías de tiendas durante las reindexaciones o las acciones masivas con un gran número de productos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6. Estos problemas están programados para solucionarse en Adobe Commerce 2.4.2.
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977: productos que faltan en las categorías, relacionados con la indexación

El parche MDVA-30977 soluciona los problemas con los productos mostrados en las páginas de categorías de tiendas durante las reindexaciones o las acciones masivas con un gran número de productos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 está instalado. Estos problemas están programados para solucionarse en Adobe Commerce 2.4.2.

## Productos y versiones afectados

El parche se ha creado para Adobe Commerce en la infraestructura en la nube 2.3.4. También es compatible con Adobe Commerce local 2.3.4.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problemas

### Problema 1

El número de productos que se muestra en la página de categoría de la tienda es diferente después de que cada página se vuelva a cargar durante la actualización masiva de productos.

<u>Pasos a seguir:</u>

1. Cree al menos 30000 productos en dos categorías, al menos 15000 productos en cada categoría.
1. Ir a **Catálogo** > **Productos** en el Administrador de comercio.
1. Seleccione todos los productos de la cuadrícula y realice una actualización masiva de atributos. Por ejemplo, set **Nuevo** = *Sí* atributo.
1. Ejecute el trabajo cron de Magento utilizando `bin/magento cron:run` dos veces.
1. Actualice las páginas de categorías en Storefront mientras Adobe Commerce realiza la actualización de productos 30000.

<u>Resultado esperado:</u>

El número de productos en categorías siempre se 15000 en cada actualización de página de categoría.

<u>Resultado real:</u>

El número de productos en las categorías es diferente en cada actualización de página de categoría.

### Problema 2

Cuando se ejecuta la reindexación completa del inventario, las páginas de categoría quedan vacías y la variable *No podemos encontrar productos que coincidan con la selección* se muestra el mensaje.

<u>Pasos a seguir:</u>

1. Configure Adobe Commerce con Elasticsearch.
1. Añada un nuevo sitio web.
1. Cree un nuevo origen y asígnelo al nuevo sitio web mediante Administrar stock.
1. Cree 30000 productos configurables.
1. Asigne todos los productos al nuevo sitio web y agregue inventario al nuevo origen de inventario.
1. Ejecute una reindexación completa.
1. Ejecute el reíndice de inventario ejecutando `bin/magento indexer:reindex inventory`
1. Examine una categoría con un gran número de productos.

<u>Resultado esperado:</u>

Las páginas de categorías muestran los productos como de costumbre durante la reindexación.

<u>Resultado real:</u>

Las páginas de categoría quedan vacías durante la reindexación.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
