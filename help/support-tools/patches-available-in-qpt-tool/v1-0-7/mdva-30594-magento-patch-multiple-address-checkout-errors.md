---
title: "MDVA-30594: errores de desprotección de varias direcciones"
description: El parche MDVA-30594 resuelve el problema en el que el cliente no ve la página de éxito del pedido después de realizar un pedido con varias direcciones. Al comprobar los pedidos en el administrador de Commerce, se muestran dos pedidos con los mismos productos en lugar de los productos correctos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. El problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594: errores de comprobación de varias direcciones

El parche MDVA-30594 resuelve el problema en el que el cliente no ve la página de éxito del pedido después de realizar un pedido con varias direcciones. Al comprobar los pedidos en el administrador de Commerce, se muestran dos pedidos con los mismos productos en lugar de los productos correctos. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalado. El problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los pedidos con varias direcciones no se completan con la página de éxito del pedido y muestran dos pedidos con los mismos productos en lugar de los correctos.

<u>Requisitos previos</u>:

Cree dos sitios web con tiendas y vistas de tiendas.

<u>Pasos a seguir</u>:

1. Establecer **Precios de catálogo** para el catálogo del sitio web (**Tiendas** > **Configuración** > **Configuración** > **Catálogo** > **Catálogo** > **Precio** > **Ámbito**).
1. Configurar **Impuestos fijos sobre productos (FPT)** (**Tiendas** > **Configuración** > **Ventas** > **Impuestos** > **Impuestos fijos de productos**):

   * **Habilitar FPT** = *Sí*
   * **Mostrar precios en la lista de productos** = *Exclusión de FTP*
   * **Mostrar precios en la página de vista del producto** = *Exclusión de FTP*
   * **Mostrar precios en módulos de ventas** = *Exclusión de FTP* (Incluyendo **FPT** descripción y precio final).
   * **Mostrar precios en correos electrónicos** = *Exclusión de FTP* (Incluyendo **FPT** descripción y precio final).
   * **Aplicar impuesto a FTP** = *Sí*
   * **Incluir FTP en el subtotal** = *No*

1. Crear un **Atributo FTP** y asígnelo al conjunto de atributos predeterminado. (Consulte [Configuración de FTP: Crear un atributo FTP](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) en nuestra guía del usuario).

1. Cree cuatro productos simples y configure el **FPT** **valor de atributo** (Ejemplo: configurar el **FPT**   **valor de atributo** = *Australia*).

1. Cree dos productos agrupados con la siguiente configuración:

   * Definir **FPT**.
   * Establecer **Precio dinámico** = *No*.
   * Establecer **Precio** = *100*.
   * Agrupar opciones enviadas juntas, todas marcadas como predeterminadas con **Tipo de precio** = *Fijo*.
   * Agregue dos de los productos simples creados en el paso cuatro.

1. Cree una cuenta de usuario en el front-end. Actualice la dirección con la dirección de Australia (establezca el país en Australia o el país que se haya utilizado en la **FPT** configuración).

1. Agregue los dos productos agrupados al carro de compras.

1. Vaya a la página del carro de compras y compruebe que la variable **FPT** se muestra correctamente.

1. Clic **Cierre de compra con varias direcciones**.

1. Añada una segunda dirección.

1. Asigne cada producto a una dirección diferente.

1. Continúe con el proceso de cierre de compra hasta **Realizar pedido**.

1. Haga clic en **Realizar pedido** botón.

<u>Resultados esperados</u>:

El pedido con varias direcciones se ha realizado correctamente.

<u>Resultados reales</u>:

Un mensaje como &quot;*Se ha producido un error.*&quot; aparecerá.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
