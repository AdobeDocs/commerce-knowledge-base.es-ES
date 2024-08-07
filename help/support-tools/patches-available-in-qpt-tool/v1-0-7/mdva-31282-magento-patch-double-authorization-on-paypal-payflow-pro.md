---
title: 'MDVA-31282: doble autorización en PayFlow Pro de PayPal'
description: El parche MDVA-31282 resuelve el problema cuando se producen autorizaciones dobles en PayFlow Pro de PayPal en Adobe Commerce. Las dobles autorizaciones también tienen el efecto de evitar los filtros de fraude de PayFlow Pro y duplicar las tarifas de transacción. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282: doble autorización en PayFlow Pro de PayPal

El parche MDVA-31282 resuelve el problema cuando se producen autorizaciones dobles en PayFlow Pro de PayPal en Adobe Commerce. Las dobles autorizaciones también tienen el efecto de evitar los filtros de fraude de PayFlow Pro y duplicar las tarifas de transacción. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.3.3 y 2.3.5 - 2.3.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las autorizaciones dobles se producen en PayPal PayFlow Pro en Adobe Commerce, que tiene el efecto de evitar los filtros de fraude de PayFlow Pro y duplicar las tarifas de transacción.

<u>Requisitos previos</u>:

Configura el método de pago PayPal PayFlow Pro.

<u>Pasos a seguir</u>:

1. Vaya al front-end como cliente invitado.
1. Agregar productos al **carro de compras** desde las páginas de productos.
1. Continuar con **cierre de compra**.
1. Especifique **Dirección de envío** como dirección en País \#1 (Ejemplo: Dirección de Reino Unido) y seleccione un método de envío.
1. Selecciona **PayPal PayFlow Pro** como forma de pago. Especifique la **Dirección de facturación** como una dirección en País \#2 (Ejemplo: Dirección de EE.UU.).
1. Introduzca los datos de la tarjeta de crédito y realice el pedido.
1. Vaya a **Ventas** > **Pedidos** en administración y observe el orden creado.

<u>Resultados esperados</u>:

* El bloque Información de pago muestra: *&quot;Filtros de fraude activados: RESPMSG: En revisión por el servicio de fraude*. *El pedido está en estado de Sospecha de Fraude&quot;*.
* PayFlow Pro muestra una única transacción de autorización según lo esperado.

<u>Resultados reales</u>:

* El bloque Información de pago muestra: *&quot;Filtros de fraude activados: RESPMSG: En revisión por el servicio de fraude*. *El pedido está en estado de procesamiento&quot;*.
* Paypal PayFlow Pro muestra transacciones de autorización doble.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
