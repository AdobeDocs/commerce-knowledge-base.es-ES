---
title: "MDVA-40399: Las facturas parciales para el mismo pedido no se pueden crear simultáneamente mediante API"
description: El parche MDVA-40399 corrige el problema en el que las facturas parciales del mismo pedido no se pueden crear simultáneamente mediante la API de REST. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. El ID del parche es MDVA-40399. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: Las facturas parciales para el mismo pedido no se pueden crear simultáneamente mediante API

El parche MDVA-40399 corrige el problema en el que las facturas parciales del mismo pedido no se pueden crear simultáneamente mediante la API de REST. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. El ID del parche es MDVA-40399. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* `qty_invoiced` debe actualizarse para ambas facturas en la tabla `sales_order_item`.
* Ambos productos deberían tener una cantidad facturada.

<u>Resultados reales</u>:

* Ambas facturas se han creado correctamente.
* `qty_invoiced` no se ha actualizado con una de las facturas de la tabla `sales_order_item`.
* En la página **Vista de pedidos** del administrador, la cantidad de facturas solo se muestra para un producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/usage) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
