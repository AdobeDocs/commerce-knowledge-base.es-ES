---
title: "MDVA-34591: Los cálculos de reglas de precios del carro de compras no son los esperados"
description: El parche MDVA-34591 corrige el problema de que la regla de precio del carro de compras con **Descuento máximo de cantidad se aplica a** no funciona correctamente si se aplican varias reglas de precio del carro de compras. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-34591. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591: Los cálculos de reglas de precios del carro de compras no son los esperados

El parche MDVA-34591 corrige el problema en el que la regla de precio del carro de compras con **El descuento de cantidad máxima se aplica a** no funciona correctamente si se aplican varias reglas de precios del carro de compras. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalado. El ID del parche es MDVA-34591. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.6

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Vaya a Admin y cree las dos reglas siguientes:

   * Regla 1: 10 $ de descuento en un máximo de tres elementos del carro de compras. Establecer prioridad = *3*.
   * Regla 2: 50 % de descuento en todos los productos del carro de compras. Establecer prioridad = *1*.

1. Ve a la tienda.

1. Agregar ocho cantidades de un conjunto de productos a precio = *51 $* cada uno al carro de compras.

1. Compruebe el importe del descuento en el carro de compras.

<u>Resultados esperados</u>:

El descuento calculado correcto es de 234 $, tal como se esperaba.

* Cálculos:

  Reglas de precios de carro de compras coincidentes: Regla 2, Regla 1\
  Aplicar regla 2 (50% de descuento), por lo que Descuento = 204 $\
  Aplicar regla 1 (10 de 3 elementos), por lo que Descuento = 30 $\
  Descuento total = MIN ( 408/2 + 10x3, 8 &#42; 51) = MÍN. (204 + 30, 8 &#42; 51) = 234 $

<u>Resultados reales</u>:

El descuento se calcula incorrectamente en 153 $, debido a que la cantidad utilizada para calcular el valor de descuento máximo es incorrecta, ya que el importe de descuento fijo se aplica independientemente del importe de los productos en el carro de compras.

* Cálculos:

  Reglas de precios de carro de compras coincidentes: Regla 2, Regla 1\
  Aplicar regla 2 (50% de descuento), por lo que Descuento = 204 $\
  Aplicar regla 1 (10 de 3 elementos), por lo que Descuento = 30 $\
  Descuento total = MIN (204 + 30, 3 &#42; 51) = 153 $

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
