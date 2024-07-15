---
title: "MDVA-30845: el cierre de compra interrumpe la conexión con el proveedor de envío"
description: El parche de MDVA-30845 soluciona el problema de que el error *Lo sentimos, no hay presupuestos disponibles para este pedido en este momento* se muestra al no conectarse a UPS XML/USPS/DHL durante el cierre de compra y no hay ningún otro método de envío disponible. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.2.
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845: el cierre de compra interrumpe la conexión con el proveedor de envío

El parche de MDVA-30845 soluciona el problema en el que el error *Lo sentimos, no hay presupuestos disponibles para este pedido en este momento* se muestra al no conectarse a UPS XML/USPS/DHL durante el cierre de compra y no hay ningún otro método de envío disponible. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.3.5-p2.

**Compatible con versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.5-2.3.6.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Durante el proceso de pago y envío, el error *Lo sentimos, no hay ofertas disponibles para este pedido en este momento* se muestra cuando no se puede conectar a UPS XML/USPS/DHL, y no hay ningún otro método de envío disponible.

<u>Pasos a seguir:</u>

1. Cree un producto.
1. Habilite y configure el método de envío XML de UPS.
1. Añadir el producto al carro de compras en la tienda.
1. Asegúrese de que los métodos de envío de UPS y el envío a tarifa plana estén disponibles.
1. Edite el archivo de hosts para evitar que USP se conecte a su puerta de enlace.
1. En el frente de la tienda, trate de obtener las tarifas y proceda a pagar de nuevo.

<u>Resultado real:</u>

*Lo sentimos, no hay ofertas disponibles para este pedido en este momento* se muestra el error y el envío de tarifa plana no está disponible.

<u>Resultado esperado:</u>

No se muestra ningún mensaje de error y el envío a tarifa única está disponible.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.


## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
