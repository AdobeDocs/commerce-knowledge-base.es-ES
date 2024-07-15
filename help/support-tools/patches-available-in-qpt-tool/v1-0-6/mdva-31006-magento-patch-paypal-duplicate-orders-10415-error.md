---
title: "MDVA-31006: Error de 10415 de pedidos duplicados de Paypal"
description: El parche MDVA-31006 soluciona el problema de que el uso del pago por pago y envío de PayPal Express crea pedidos duplicados con un error 10415. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. El problema se solucionó en Adobe Commerce 2.4.2.
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006: error de 10415 de pedidos duplicados de PayPal

El parche MDVA-31006 soluciona el problema de que el uso del pago por pago y envío de PayPal Express crea pedidos duplicados con un error 10415. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. El problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.4.0

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario no se envía a la página de pedidos correctos de Adobe Commerce, por lo que actualiza la página en blanco y se realiza el segundo pedido, lo que provoca la duplicación de pedidos.

<u>Requisitos previos</u>:

* Adobe Commerce está instalado.
* El pago mediante pago y envío de PayPal Express está configurado.
* Inicie sesión en Commerce admin. Vaya a **Tiendas** > **Configuración** > **Ventas** > **Métodos de pago** > seleccione **Cierre de compra de PayPal Express** > **Configurar** > **Configuración avanzada** > **Omitir paso de revisión de pedido** > *No*.

<u>Pasos a seguir</u>:

1. Inicie sesión como usuario.
1. Seleccione un elemento y haga clic en **Agregar al carro**.
1. Haga clic en el carrito y luego en **Continuar con la compra**.
1. Acceda a la ventana PayPal Express y realice un pago.
1. Se le redirigirá a la página de revisión de pedidos de Adobe Commerce.
1. Presione el botón **Realizar pedido**.
1. Error del sistema de emulación debido a problemas de infraestructura del servidor. El usuario verá una página en blanco.
1. Actualice la página.

<u>Resultados esperados</u>:

* Se redirige al cliente a la página de revisión de pedidos y aparece un mensaje de error &quot;*Ya se ha completado una transacción de pago correcta. Compruebe si se ha realizado el pedido.*&quot;
* En el archivo payment.log, que se encuentra en `/var/log/payment.log`, hay un 10415 de error, pero solo se creó un pedido.

<u>Resultados reales</u>:

* Como el cliente no se envía a la página de éxito de pedidos de Adobe Commerce, actualiza la página en blanco y se realiza un segundo pedido, por lo que se crean dos pedidos duplicados.
* En el archivo payment.log, que se encuentra en `/var/log/payment.log`, hay un 10415 de error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
