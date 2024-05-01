---
title: "MDVA-37916: Pagos mediante PayPal avanzados que no vuelven a la página de confirmación"
description: El parche de calidad MDVA-37916 para Adobe Commerce soluciona el problema de que Pagos mediante PayPal Avanzados no vuelve a la página de confirmación después del pago. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. El ID del parche es MDVA-37916. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916: Pagos mediante PayPal avanzados que no vuelven a la página de confirmación

El parche de calidad MDVA-37916 para Adobe Commerce soluciona el problema de que Pagos mediante PayPal Avanzados no vuelve a la página de confirmación después del pago. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalado. El ID del parche es MDVA-37916. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
Adobe Commerce en infraestructura en la nube 2.3.6-p1

**Compatible con las versiones de Adobe Commerce:**
Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.6-2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El cliente no será llevado a la página de confirmación de pago después del pago cuando utilice el método avanzado de pagos de PayPal.

<u>Pasos a seguir</u>: [Screencast](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. Añada el producto al carro de compras y navegue hasta el paso de pago de la página de cierre de compra.
1. Seleccionar **Tarjeta de Crédito (Flujo de Pago Avanzado)** opción de pago.
1. Clic **Continuar** para que aparezca el iframe con el formulario de pago.
1. Rellene el formulario de pago con los datos de la tarjeta de crédito de la zona protegida.
   * Número de tarjeta: 4444 3333 2222 1111 o 4111 111 111 111 111 111
   * Fecha de caducidad: 23/12
   * CSC: 123
1. Clic **Pagar ahora**.

<u>Resultados esperados</u>:

Una vez procesado el pago y realizado el pago correctamente, se le redirigirá a la página de confirmación del pedido.

<u>Resultados reales</u>:

* NO se le redirigirá a la página de confirmación de pedido.
* Pero el pedido se ha creado en Adobe Commerce.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad en nuestra base de conocimiento de asistencia, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) en nuestra base de conocimiento de asistencia.
