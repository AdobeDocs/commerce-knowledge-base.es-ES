---
title: "MDVA-37068: Impuesto incorrecto mostrado en el cierre de compra de productos virtuales"
description: El parche MDVA-37068 corrige el problema cuando la página de cierre de compra muestra una tasa de impuestos incorrecta para productos virtuales. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. El ID del parche es MDVA-37068. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068: Impuesto incorrecto mostrado en el cierre de compra de productos virtuales

El parche MDVA-37068 corrige el problema cuando la página de cierre de compra muestra una tasa de impuestos incorrecta para productos virtuales. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 está instalado. El ID del parche es MDVA-37068. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con las versiones de Adobe Commerce:**
Adobe Commerce (todos los métodos de implementación) 2.3.1-2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La tasa de impuestos incorrecta se muestra en la página de cierre de compra cuando el carro de compras solo tiene productos virtuales.

<u>Requisitos previos</u>:

1. Cree dos tipos impositivos y reglas fiscales independientes para dos países diferentes: por ejemplo, el 10 % y el 1 %.
1. Cree un producto virtual.
1. Ejecute reindex y limpie la caché.

<u>Pasos a seguir</u>:

1. Crear un cliente.
1. Añadir direcciones de facturación y envío diferentes.
1. Agregar un producto virtual al carro de compras.
1. Compruebe el carro de compras y la página de cierre de compra.

<u>Resultados esperados</u>:

Los impuestos mostrados en la página Carro de compras y Cierre de compra son los mismos.

<u>Resultados reales</u>:

Los impuestos mostrados en el carro de compras y en la página de cierre de compra NO son iguales.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
