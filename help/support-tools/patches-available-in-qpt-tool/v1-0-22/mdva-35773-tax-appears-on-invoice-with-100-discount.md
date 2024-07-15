---
title: 'MDVA-35773: Los impuestos aparecen en la factura con un descuento del 100%'
description: El parche de MDVA-35773 soluciona el problema de que el total general no aparece como cero en la factura de pedidos con un descuento del 100%. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. El ID del parche es MDVA-35773. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773: Los impuestos aparecen en la factura con un descuento del 100%

El parche de MDVA-35773 soluciona el problema de que el total general no aparece como cero en la factura de pedidos con un descuento del 100%. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. El ID del parche es MDVA-35773. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.6

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.6-2.3.7 y 2.4.1-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Vaya a **Tiendas** > **Configuración** > **Configuración** > **Ventas** > **Impuestos**.
1. Establecer **precios de catálogo** y **Aplicar descuento en precios** a *Impuestos incluidos*.
1. Vaya a **Tiendas** > **Reglas fiscales** > **Agregar nueva regla fiscal**.
1. Cree una regla fiscal (por ejemplo, todos los EE. UU. con una tasa impositiva del 10 %) y aplíquela.
1. Vaya a **Marketing** > **Reglas de precio del carro de compras** y **Agregar nueva regla**.
1. Cree una regla con un **100% de descuento para todos los usuarios**.
1. Haz un pedido en la Tienda:

   * Elija **Envío gratuito**.
   * Aplicar **Código De Cupón**.

1. Vaya a **Ventas** > **Pedidos** y abra el pedido.
1. Cree una factura para el pedido y ábrala.

<u>Resultados esperados</u>:

Total general de la factura = *$0,00*.

<u>Resultados reales</u>:

Se crea el total general de la factura = *importe de impuestos*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
