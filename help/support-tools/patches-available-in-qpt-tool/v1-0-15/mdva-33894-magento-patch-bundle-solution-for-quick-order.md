---
title: "Parche MDVA-33894: paquete de soluciones para pedidos rápidos"
description: El parche MDVA-33894 soluciona varios problemas relacionados con la función de orden rápido, como añadir y eliminar varios productos y la distinción de mayúsculas y minúsculas en las SKU. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: d0b18e71-5f48-441e-a8b9-c459f3d34599
feature: Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Parche MDVA-33894: paquete de soluciones para pedidos rápidos

El parche MDVA-33894 soluciona varios problemas relacionados con la función de orden rápido, como añadir y eliminar varios productos y la distinción de mayúsculas y minúsculas en las SKU. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalado. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en infraestructura en la nube 2.4.0

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.4.0-2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El parche MDVA-33894 es un paquete de soluciones para los siguientes problemas:

* **Mi cuenta** > **Ordenar por SKU** La funcionalidad distingue entre mayúsculas y minúsculas: si introduce un SKU válido pero el uso de mayúsculas y minúsculas no es correcto (mayúsculas en lugar de minúsculas, etc.), Adobe Commerce genera un error.
* Cuando un comprador utiliza Pedidos rápidos para agregar varios productos al carro de compras e intenta eliminar un producto, este no se elimina.
* Problemas de distinción de mayúsculas y minúsculas al añadir varias SKU a un pedido masivo.
* Problema de caché de la página Pedido rápido con SKU introducidas anteriormente.
* La cantidad de pedido rápido no se refleja en el carro de compras.
* La duplicación de SKU no se ha validado correctamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
