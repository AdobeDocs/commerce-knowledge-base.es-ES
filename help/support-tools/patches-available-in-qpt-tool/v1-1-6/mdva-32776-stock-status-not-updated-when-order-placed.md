---
title: "MDVA-32776: El estado de las existencias no se actualiza con la realización del pedido"
description: El parche MDVA-32776 soluciona el problema de que el estado de las existencias no se actualiza cuando se realiza un pedido, pero no se envía. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6. El ID del parche es MDVA-32776. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776: El estado de las existencias no se actualiza con la realización del pedido

El parche MDVA-32776 soluciona el problema de que el estado de las existencias no se actualiza cuando se realiza un pedido, pero no se envía. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 está instalado. El ID del parche es MDVA-32776. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.0

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de stock no se actualiza cuando se realiza un pedido, pero no se envía.

<u>Requisitos previos</u>:

1. Módulo de inventario instalado.
1. Mostrar productos sin existencias está establecido en *Sí*.

   Para configurarlo, vaya a **Tiendas** > **Configuración** > **Catálogo** > **Inventario** > **Mostrar productos sin existencias** = *Sí*.

<u>Pasos a seguir</u>:

1. Cree dos productos simples con qty = 11 y 22.
1. Cree un producto agrupado con los productos simples creados en el paso uno.
1. Añada productos agrupados al carro de compras estableciendo una de las cantidades de productos en 11 y haciendo que el otro producto simple se quede sin existencias.
1. Complete el cierre de compra y realice el pedido.

<u>Resultados esperados</u>:

Se muestran los productos agrupados `out-of-stock` etiquetas cuando los productos simples asociados se quedan sin existencias.

<u>Resultados reales</u>:

1. El producto simple con cantidad = 11 muestra sin existencias.
1. El producto agrupado no muestra un *agotado* mensaje para el producto con cantidad = 11. Sin embargo, al agregar este producto al carro de compras se obtiene una *agotado* error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
