---
title: "MDVA-30428: la lista de deseos no funciona con Inventory management"
description: El parche MDVA-30428 resuelve la lista de deseos que no funciona con Inventory management (MSI). Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5.
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428: la lista de deseos no funciona con Inventory management

El parche MDVA-30428 resuelve la lista de deseos que no funciona con Inventory management (MSI). Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3 - 2.3.3-p1 (QPT 1.0.6) y 2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al agregar un producto a la lista de deseos, cuando el producto se asigna a un origen de inventario personalizado, el siguiente mensaje muestra &quot;*No podemos agregar el producto a la Lista de deseos en este momento: No se puede agregar el producto sin existencias a la lista de deseos.*&quot;

<u>Pasos a seguir</u>:

1. Cree un nuevo origen de inventario en el administrador de Commerce. Para ver los pasos, consulte [Catálogo > Agregar un nuevo Source](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) en nuestra guía del usuario.
1. Cree un nuevo inventario de existencias en el administrador de Commerce y asigne el nuevo origen y el sitio web predeterminado a las nuevas existencias. Para ver los pasos, consulte [Catálogo > Agregar un nuevo inventario](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) en nuestra guía del usuario.
1. Cree un producto simple y asigne solo el nuevo inventario de stock.
1. Visite la página de detalles simples del producto en el front-end.
1. Añadir el producto a la lista de deseos. El siguiente error muestra: *No podemos agregar el artículo a la Lista de deseos en este momento: No se puede agregar un producto sin existencias a la Lista de deseos*.

<u>Resultados esperados</u>:

El producto debe añadirse a la lista de deseos con el stock personalizado.

<u>Resultados reales</u>:

El producto no se añade a la lista de deseos y aparece un mensaje de error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
