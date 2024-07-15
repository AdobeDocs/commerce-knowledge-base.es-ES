---
title: "MDVA-29400: Pedidos duplicados realizados con el pago y envío de PayPal Express"
description: El parche de MDVA-29400 soluciona el problema en el que se crean pedidos duplicados cuando los clientes realizan pedidos con el Pago y envío de PayPal Express. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. El ID del parche es MDVA-29400. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400: pedidos duplicados realizados con el pago y envío de PayPal Express

El parche de MDVA-29400 soluciona el problema en el que se crean pedidos duplicados cuando los clientes realizan pedidos con el Pago y envío de PayPal Express. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. El ID del parche es MDVA-29400. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los pedidos duplicados se crean cuando los usuarios realizan pedidos con Pago y envío de PayPal Express.

<u>Requisitos previos</u>:

Pago y envío por PayPal Express activado y configurado.

<u>Pasos a seguir</u>:

1. Añadir un producto al carro de compras.
1. Ve a la página de pago y utiliza PayPal Express como forma de pago.
1. Se redirigirá a paypal/express/review/ page.
1. Realice el pedido. Se le redirigirá a la página de éxito.
1. Vuelve a PayPal/express/review/Page.
1. Haz clic en el botón **Realizar pedido**.

<u>Resultados esperados</u>:

Solo se crea un pedido.

<u>Resultados reales</u>:

Recibe el siguiente error: *El token de pago y envío de PayPal Express no existe*, pero el segundo pedido se realizó correctamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
