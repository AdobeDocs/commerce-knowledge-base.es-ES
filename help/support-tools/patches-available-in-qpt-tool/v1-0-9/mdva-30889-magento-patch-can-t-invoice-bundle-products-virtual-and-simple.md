---
title: "MDVA-30889: No se puede facturar paquete de productos virtual y simple"
description: El parche MDVA-30889 soluciona el problema en el que se produce un error después de facturar un producto agrupado con opciones tanto virtuales como simples. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 7e6555c5-9088-4c85-920d-20c841ad6675
feature: Invoices, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-30889: No se puede facturar un paquete de productos virtual y simple

El parche MDVA-30889 soluciona el problema en el que se produce un error después de facturar un producto agrupado con opciones tanto virtuales como simples. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisitos previos</u>:

Instalación de Adobe Commerce con [Inventory management](https://devdocs.magento.com/guides/v2.4/inventory/).

<u>Pasos a seguir</u>:

1. Ir a **Administrador**.
1. Cree un producto sencillo.
1. Cree un producto virtual.
1. Cree un producto agrupado (cree dos opciones desplegables para productos secundarios y asigne productos virtuales y simples). Establecer **Precio dinámico** = *No*.
1. Ve a la tienda.
1. Vaya a la página del producto.
1. Añadir el producto al carro de compras.
1. Continúe con el cierre de compra y solicite el producto.
1. Ir a **Administración > Pedidos**.
1. Abra el pedido creado y factura.

<u>Resultados esperados</u>:

Se crea la factura de un producto agrupado (que contiene productos simples y virtuales).

<u>Resultados reales</u>:

La factura no se ha creado y recibirá un error similar al siguiente:

```php
TypeError: Return value of Magento\InventorySourceSelection\Model\Request\InventoryRequest::getItems() must be of the type array, null returned in vendor/magento/module-inventory-source-selection/Model/Request/InventoryRequest.php:102
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
