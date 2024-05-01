---
title: 'Parche ''MDVA-31399: subtotal (incl. Impuestos) en la condición de regla de carro de compras'
description: El parche MDVA-31399 suma el subtotal *Subtotal (incl. Opción de impuestos)* para [condición de regla de precio de carro de compras](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), solucionando el problema donde era imposible aplicar una regla de precio de carro de compras basada en el subtotal (incl. Número de IVA). Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12.
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Parche MDVA-31399: subtotal (incl. Impuestos) en la condición de regla del carro

El parche MDVA-31399 añade el *Subtotal (incl. Tax)* opción para [condición de regla de precio de carrito](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), solucionando el problema donde era imposible aplicar una regla de precio de carrito basada en Subtotal (Incl. Número de IVA). Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 está instalado.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.2 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Es imposible aplicar una regla de precio de carro basada en Subtotal (Incl. Número de IVA).

<u>Pasos a seguir</u>:

1. Configure el precio del producto para incluir impuestos.
1. Cree una regla fiscal y una tasa impositiva del 20%.
1. Cree un producto con **Precio** = *100* (este precio incluye impuestos).
1. Cree una nueva regla de precio del carro de compras con un cupón &quot;10 de descuento&quot; al que aplicar un descuento fijo de 10 $ si el subtotal cumple estas condiciones:

**Condiciones**: *Si TODAS estas condiciones son VERDADERAS:*        * **Subtotal** igual o mayor que 100.*

<u>Resultados esperados</u>:

Puede crear una regla de precio de carro de subtotales con cupón para aplicar descuento al subtotal, incluidos los impuestos.

<u>Resultados reales</u>:

Existen dos opciones en las condiciones de regla del carro de compras: *Subtotal* y *Subtotal (excl. Tax)* y cualquiera que sea la seleccionada, la regla se aplica solo al subtotal sin incluir impuestos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
