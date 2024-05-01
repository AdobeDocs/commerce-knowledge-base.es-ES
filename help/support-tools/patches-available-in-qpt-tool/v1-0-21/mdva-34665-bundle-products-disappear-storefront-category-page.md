---
title: "MDVA-34665: los productos agrupados desaparecen de la página de categoría de tienda"
description: El parche MDVA-34665 soluciona el problema de los productos agrupados que faltan en las páginas de categorías. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. El ID del parche es MDVA-34665. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665: los productos agrupados desaparecen de la página de categoría de tienda

El parche MDVA-34665 soluciona el problema de los productos agrupados que faltan en las páginas de categorías. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalado. El ID del parche es MDVA-34665. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.4-p2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.4-2.3.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

**Caso 1:**

<u>Requisitos previos</u>:

1. Cree 15.000 productos agrupados con un producto simple como opción de paquete. No utilice el mismo producto simple con varios productos agrupados.
1. Los productos simples deben configurarse como *No visible individualmente*.

<u>Pasos a seguir</u>:

1. Asigne 15.000 productos agrupados en dos categorías, 7.500 cada una.
1. Seleccione todos los productos simples (15 000) y actualice el stock mediante las actualizaciones de atributos de masa de productos. Nuestro objetivo es tener muchos ID en la tabla de búsqueda de cq (las tablas de cq son las tablas que usa el indizador para saber qué registros deben actualizarse).
1. Asegúrese de que tiene 15.000 ID en `catalogsearch_fulltext_cl` tabla.
1. Asegúrese de que la `indexer_update_all_views` se ejecuta el indexador.
1. Consulte la página de categoría continuamente y observe el recuento de productos.

<u>Resultados esperados</u>:

El recuento de productos debe permanecer como estaba después de la reindexación.

<u>Resultados reales</u>:

El recuento de productos cae a 7.450 después de un tiempo. Permanece en 7450 incluso después de finalizar la indexación.

**Caso 2:**

<u>Pasos a seguir</u>:

1. Cree un paquete de productos con un producto simple asociado como opción.
1. Cambie los modos del indexador a *actualizar según lo programado*.
1. Asigne el producto del paquete a una categoría.
1. Cambie el estado de stock del producto simple a *sin existencias*.
1. Ejecute cron; el producto del paquete desaparece de la tienda.
1. Vuelva a añadir existencias al producto simple y guarde.
1. Ejecute el indexador cron.
1. Actualice la página de categoría.

<u>Resultados esperados</u>:

El producto sigue ausente.

<u>Resultados reales</u>:

El producto del paquete vuelve a aparecer.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
