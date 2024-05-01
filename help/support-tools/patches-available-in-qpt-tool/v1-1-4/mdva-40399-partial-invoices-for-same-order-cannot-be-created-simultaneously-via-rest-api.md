---
title: "MDVA-40399: Las facturas parciales para el mismo pedido no se pueden crear simultáneamente mediante API"
description: El parche MDVA-40399 corrige el problema en el que las facturas parciales del mismo pedido no se pueden crear simultáneamente mediante la API de REST. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4. El ID del parche es MDVA-40399. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: Las facturas parciales para el mismo pedido no se pueden crear simultáneamente mediante API

El parche MDVA-40399 corrige el problema en el que las facturas parciales del mismo pedido no se pueden crear simultáneamente mediante la API de REST. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 está instalado. El ID del parche es MDVA-40399. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se pueden crear simultáneamente facturas parciales para los mismos pedidos mediante la API de REST.

<u>Requisitos previos</u>:

Un producto configurable con al menos dos variaciones.

<u>Pasos a seguir</u>:

1. Añada ambas variantes del producto configurable al carro de compras.
1. Realice el pedido.
1. Cree dos facturas simultáneamente para el pedido a través de la API REST.

<u>Resultados esperados</u>:

* Ambas facturas deben crearse correctamente.
* `qty_invoiced` debe actualizarse para ambas facturas en el `sales_order_item` tabla.
* Ambos productos deberían tener una cantidad facturada.

<u>Resultados reales</u>:

* Ambas facturas se han creado correctamente.
* `qty_invoiced` no se actualiza con una de las facturas de `sales_order_item` tabla.
* En el del administrador **Vista de pedidos** página, la cantidad de facturas solo se muestra para un producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
