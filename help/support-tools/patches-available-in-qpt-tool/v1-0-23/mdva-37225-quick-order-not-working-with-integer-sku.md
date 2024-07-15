---
title: "MDVA-37225: El pedido rápido no funciona con el SKU entero"
description: El parche de calidad MDVA-37225 para Adobe Commerce soluciona el problema de que la página no se carga al crear un pedido rápido si hay un valor entero en los SKU importados. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. El ID del parche es MDVA-37225. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225: El pedido rápido no funciona con el SKU entero

El parche de calidad MDVA-37225 para Adobe Commerce soluciona el problema de que la página no se carga al crear un pedido rápido si hay un valor entero en los SKU importados. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. El ID del parche es MDVA-37225. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

* El parche se ha diseñado para Adobe Commerce en la infraestructura en la nube 2.4.1-p1
* El parche también es compatible con Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.1-2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Requisito previo</u>:

Adobe Commerce con módulo B2B instalado

<u>Pasos a seguir</u>:

1. Habilitar la funcionalidad de pedidos rápidos B2B.
1. Cree 4 productos sencillos con SKU (ejemplo de SKU: *00100*, *001E002*, *001E02C* y *7100824*).
1. Vaya a la página ``<storefront_url>/quickorder`` en el front-end e intente crear un pedido con un archivo CSV con el siguiente contenido de ejemplo:

| sku | cantidad |
|---|---|
| 00100 | 1 |


<u>Resultados esperados</u>:

El producto (Ejemplo: producto con SKU = *00100*) se agrega al carro de compras, según lo esperado.

<u>Resultados reales</u>:

La página no se carga y no se agregan productos al carro de compras.


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en nuestra documentación para desarrolladores, según el producto de Adobe Commerce:

* Adobe Commerce y Magento Open Source locales: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad en nuestra base de conocimiento de asistencia, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) de nuestra base de conocimiento de asistencia.
