---
title: "Parche MDVA-33382: indizadores invalidados"
description: El parche MDVA-33382 resuelve el problema cuando los indexadores se invalidan después de agregar, eliminar o reordenar productos en una categoría. Los indexadores que se invalidan son catalog_category_product , catalogsearch_fulltext (y sus dependientes).
exl-id: b4ac10ee-0f9d-4d7a-be72-c4d90ebadb10
feature: Catalog Management, Categories, Price Indexer
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Parche MDVA-33382: indexadores invalidados

El parche MDVA-33382 resuelve el problema cuando los indexadores se invalidan después de agregar, eliminar o reordenar productos en una categoría. Los indexadores que se invalidan son `catalog_category_product` , `catalogsearch_fulltext` (y sus dependientes).

Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 está instalado. Tenga en cuenta que el problema se solucionará en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en infraestructura en la nube 2.3.4-p2

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Establezca todos los modos del indexador de índices en **Actualización según lo programado**.
1. Eliminar un producto de una página de edición de categorías.
1. Guarde la categoría.
1. Compruebe el estado de los índices en el servidor o en CLI.

<u>Resultados esperados</u>:

Los siguientes índices no se invalidan: `catalog_category_product` , `catalogsearch_fulltext` (y sus dependientes), como se esperaba.

<u>Resultados reales</u>:

Los siguientes índices se invalidan: `catalog_category_product` , `catalogsearch_fulltext` (y sus dependientes).

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
