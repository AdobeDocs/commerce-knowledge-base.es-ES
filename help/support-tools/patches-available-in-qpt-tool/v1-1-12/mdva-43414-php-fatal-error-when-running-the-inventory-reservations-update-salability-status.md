---
title: 'MDVA-43414: Error grave de PHP al ejecutar "inventory.booking.updateSalabilityStatus"'
description: El parche MDVA-43414 resuelve el error grave de PHP que se produce al ejecutar el consumidor de cola "inventory.booking.updateSalabilityStatus" en los SKU numéricos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. El ID del parche es MDVA-43414. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 197c5db1-36bc-41a7-a5ca-f026600da786
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-43414: Error grave de PHP al ejecutar &quot;inventory.booking.updateSalabilityStatus&quot;

El parche MDVA-43414 resuelve el error fatal de PHP que ocurre cuando se ejecuta el `inventory.reservations.updateSalabilityStatus` poner en cola al consumidor con SKU numéricas. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalado. El ID del parche es MDVA-43414. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.6 - 2.3.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error grave de PHP al ejecutar el consumidor de cola &quot;inventory.booking.updateSalabilityStatus&quot; en SKU numéricas.

<u>Requisitos previos</u>:

Módulos de inventario instalados.

<u>Pasos a seguir</u>:

1. Crear un origen de inventario personalizado y asignarlo a un nuevo inventario de stock.
1. Cree un producto con el origen de inventario personalizado.
1. Asegúrese de que el SKU del producto sea un valor entero.
1. Haga un pedido.
1. Ejecute el `bin/magento queue:consumer:start inventory.reservations.updateSalabilityStatus` comando.

<u>Resultados esperados</u>:

La cola se inicia sin ningún error.

<u>Resultados reales</u>:

Error grave de PHP:

```PHP
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to Magento\InventoryIndexer\Model\Queue\UpdateIndexSalabilityStatus\IndexProcessor::getIndexSalabilityStatus() must be of the type string, int given, called in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php on line 119 and defined in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php:136
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
