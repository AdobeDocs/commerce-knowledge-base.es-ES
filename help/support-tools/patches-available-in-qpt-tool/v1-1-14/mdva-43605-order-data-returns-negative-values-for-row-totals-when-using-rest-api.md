---
title: "MDVA-43605: Los datos de pedidos devuelven valores negativos para los totales de fila al utilizar la API de REST"
description: El parche MDVA-43605 corrige el problema en el que los datos de pedidos devuelven valores negativos para los totales de filas al utilizar la API de REST. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. El ID del parche es MDVA-43605. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605: Los datos de pedidos devuelven valores negativos para los totales de fila al utilizar la API de REST

El parche MDVA-43605 corrige el problema en el que los datos de pedidos devuelven valores negativos para los totales de filas al utilizar la API de REST. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. El ID del parche es MDVA-43605. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.1 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los datos del pedido devuelven valores negativos para los totales de fila al utilizar la API de REST.

<u>Pasos a seguir</u>:

1. Habilitar el envío gratuito.
1. Vaya a **Configuración** > **Catálogo** > **Precio** > y establezca el ámbito del precio del catálogo = Sitio web.
1. Vaya a **Configuración** > **Ventas** > **Impuestos** y actualice:
   * Clase De Impuesto Para Envío = Productos Imponibles
   * Configuración de cálculo:
      * Precio de catálogo = Impuestos incluidos
      * Precio de envío = Precio incluido
      * Aplicación De Descuentos En Precios = Impuestos Incluidos
   * Configuración de Visualización de Precios: Incluyendo Impuestos (todos los campos)
   * Configuración de visualización del carro de compras: Impuestos incluidos (todos los campos)
   * Pedidos, Facturas, Notas de Abono:
      * Mostrar importe de envío = Impuestos incluidos
1. Cree un tipo impositivo para EE. UU. (Estado = &#39;*&#39;), Porcentaje de tipo = 24,00
1. Cree una regla fiscal con el tipo impositivo anterior.
1. Cree una regla de precio de carro de compras con un cupón específico y Descuento = 50 $ de la Cantidad fija para todo el carro de compras.
1. Cree cuatro productos con los siguientes precios: 8,90, 5,90, 6,90 y 5,95 $.
1. Cree un pedido de administrador que incluya cuatro de estos productos utilizando el código de cupón creado en el paso anterior. Utiliza el envío gratuito.
1. No se requiere el pago, ya que el código de cupón cubre el total del carrito.
1. Recupere el pedido que acaba de crear mediante el punto final de la API de REST:

   ```json
   GET rest/V1/orders/1
   ```

<u>Resultados esperados</u>:

Los valores de `base_row_total` y `base_row_total_incl_tax` en la respuesta son cero.

<u>Resultados reales</u>:

Los campos `base_row_total` y `base_row_total_incl_tax` de la respuesta tienen valores negativos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
