---
title: "MDVA-40609: Datos de productos desactivados ausentes en la tabla cataloginventory_stock_status"
description: El parche MDVA-40609 resuelve el problema en el que los datos de productos desactivados no se muestran en la tabla de índice cataloginventory_stock_status, lo que provoca la visualización de cantidades de productos incorrectas. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. El ID del parche es MDVA-40609. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609: datos de productos desactivados ausentes en la tabla cataloginventory_stock_status

El parche MDVA-40609 resuelve el problema en el que los datos de los productos desactivados no se muestran en la `cataloginventory_stock_status` tabla de índice que lleva a mostrar cantidades de producto incorrectas. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 está instalado. El ID del parche es MDVA-40609. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los datos de productos desactivados no se muestran en la `cataloginventory_stock_status` tabla de índice que lleva a mostrar cantidades de producto incorrectas.

<u>Requisitos previos</u>:

Módulo de inventario instalado.

<u>Pasos a seguir</u>:

1. Configurar dos sitios web con tiendas y vistas de tiendas.
1. Crear un origen y un stock adicionales.
1. Añada un producto simple:
   * Establezca Habilitar producto en *No*.
   * Asigne dos orígenes con Estado de Artículo de Origen = Existencia y Cantidad mayor que cero.
1. Guarde el producto.
1. Compruebe la **Cantidad vendible del producto** pestaña.

<u>Resultados esperados</u>:

Ambos saldos han introducido valores superiores a cero.

<u>Resultados reales</u>:

Un inventario tiene un valor cero.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
