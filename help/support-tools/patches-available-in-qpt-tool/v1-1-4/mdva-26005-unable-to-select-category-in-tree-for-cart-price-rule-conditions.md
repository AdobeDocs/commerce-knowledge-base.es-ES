---
title: "MDVA-26005: No se puede seleccionar la categoría en el árbol para las condiciones de regla de precio del carro de compras"
description: El parche MDVA-26005 resuelve el problema en el que los usuarios no pueden seleccionar una categoría en el árbol de categorías para las condiciones de regla de precio del carro de compras. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. El ID del parche es MDVA-26005. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6.
exl-id: d3b8efc3-fd0a-4706-8851-4cecb7d3126a
feature: Categories, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-26005: No se puede seleccionar la categoría en el árbol para las condiciones de regla de precio del carro de compras

El parche MDVA-26005 resuelve el problema en el que los usuarios no pueden seleccionar una categoría en el árbol de categorías para las condiciones de regla de precio del carro de compras. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 está instalado. El ID del parche es MDVA-26005. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se puede seleccionar una categoría en el árbol de categorías para las condiciones de regla de precio del carro de compras.

<u>Pasos a seguir</u>:

1. Cree una nueva regla de precio del carro de compras o edite una existente.
1. Vaya a la sección Acción y elija una categoría en Condición.
1. Procese el árbol de categorías e intente elegir una categoría.

<u>Resultados esperados</u>:

Puede seleccionar una categoría.

<u>Resultados reales</u>:

No puede seleccionar una categoría debido a un error de JS.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
