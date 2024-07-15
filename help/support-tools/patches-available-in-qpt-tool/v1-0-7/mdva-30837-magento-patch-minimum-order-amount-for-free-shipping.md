---
title: "MDVA-30837: cantidad mínima del pedido para el envío gratuito"
description: El parche MDVA-30837 agrega opciones de configuración para el cálculo del envío gratuito, de modo que el usuario pueda configurar la cantidad mínima del pedido para recibir el envío gratuito en función del subtotal (o total general). Esto permite realizar personalizaciones locales de los métodos de impuestos y envío. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837: cantidad mínima de pedido para envío gratuito

El parche MDVA-30837 agrega opciones de configuración para el cálculo del envío gratuito, de modo que el usuario pueda configurar la cantidad mínima del pedido para recibir el envío gratuito en función del subtotal (o total general). Esto permite realizar personalizaciones locales de los métodos de impuestos y envío. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El parche MDVA-30837 agrega la configuración para configurar la configuración de **Cantidad mínima del pedido** y obtener envíos gratuitos según el subtotal (o total general):

* **Incluir impuesto en el importe**: *Sí/No* en la configuración del método de envío gratuito.
   * Cuando **Incluir impuesto en el importe** se establece en *Sí*, el importe mínimo del pedido se calcula como Subtotal + Impuesto - Descuento.
   * Cuando **Incluir impuesto en el importe** se establece en *No*, el importe mínimo del pedido se calcula como Subtotal - Descuento.

<u>Pasos a seguir</u>:

1. Vaya a **Tiendas** > Configuración > **Configuración** > **Ventas** > **Impuestos** y establezca lo siguiente:

   * Cálculo de impuestos basado en *Dirección de envío*
   * Habilitar comercio transfronterizo: *No*
   * Mostrar precios de productos en el catálogo: *Impuestos excluidos*
   * Mostrar precios de envío: *Impuestos excluidos*
   * Mostrar precios: *Impuestos excluidos*
   * Mostrar subtotal: *Impuestos excluidos*
   * Mostrar importe de envío: *Impuestos excluidos*
   * Mostrar precios de envoltorio para regalos: *Impuestos excluidos*
   * Mostrar precios de tarjetas impresas: *Impuestos excluidos*
   * Incluir impuestos en el total del pedido: *Sí*
   * Mostrar resumen completo de impuestos: *Sí*

1. Vaya a **Ventas** > **Configuración de envío** > **Envío gratuito** y establezca **Importe mínimo de pedido** = *30*.
1. Vaya a **Marketing** > Promociones > **Reglas de precio del carro de compras** y cree una nueva regla de precio (para ver los pasos detallados, consulte [Crear una regla de precio del carro de compras](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) en nuestra guía del usuario).

   * Código De Cupón = *Cupón Específico*.
   * Condiciones: El subtotal es igual o superior a 25 $.
   * Acciones: Envío gratuito = *Para envíos con artículos coincidentes*.

1. Crea un producto con un precio de 23,10 $.
1. Agregue el impuesto de CA a la regla fiscal predeterminada.
1. Añadir este producto al carro de compras.
1. Obtenga una cotización de envío: después de impuestos, el total general = $25.01 y se aplica el envío gratuito.
1. Aplique el código de cupón: no será válido porque el subtotal (impuestos excluidos) es de 23,10 $.

<u>Resultados esperados</u>:

Hay una configuración adicional - Incluir impuesto al importe: *Sí*/*No* en la configuración del método de envío gratuito:

* Cuando Incluir impuesto en importe está establecido en *Sí*, el importe mínimo del pedido se calcula como Subtotal + Impuesto - Descuento.
* Cuando Incluir impuesto en importe está establecido en *No*, el importe mínimo del pedido se calcula como Subtotal - Descuento.

<u>Resultados reales</u>:

La condición de regla de precio de envío gratuito solo puede basarse en el subtotal, mientras que el método de envío gratuito solo puede basarse en el total general.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
