---
title: Solución de problemas de PayPal en Adobe Commerce
description: Este artículo proporciona soluciones para problemas con el procesamiento de pagos a través de PayPal, especialmente la solución PayFlow Pro. Algunas recomendaciones de este artículo pueden parecer obvias. Le pedimos que intente las opciones de resolución de problemas que se enumeran en esta base de conocimiento e incluya toda la información en cualquier ticket que introduzca. Los ingenieros de soporte de Adobe Commerce o PayPal le pedirán que siga estos pasos a la hora de diagnosticar sus problemas.
exl-id: f0772515-8456-4f08-84b4-aeef44516f2a
feature: Orders, Payments
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Solución de problemas de PayPal en Adobe Commerce

Este artículo proporciona soluciones para problemas con el procesamiento de pagos a través de PayPal, especialmente la solución PayFlow Pro. Algunas recomendaciones de este artículo pueden parecer obvias. Le pedimos que intente las opciones de resolución de problemas que se enumeran en esta base de conocimiento e incluya toda la información en cualquier ticket que introduzca. Los ingenieros de soporte de Adobe Commerce o PayPal le pedirán que siga estos pasos a la hora de diagnosticar sus problemas.

## Problemas comunes

La mayoría de los problemas con los pagos de PayPal tienen síntomas similares: después de especificar los detalles de la tarjeta de pago y proceder al cierre de compra, el pago no se está procesando. En su lugar, puede haber un mensaje de error, un error al procesar el pago o incluso una página en blanco.

## Compruebe sus credenciales, claves de cifrado y licencias

Posibles problemas: erratas en los detalles de la cuenta (nombres de usuario, contraseñas), cuentas no válidas, licencias caducadas o no especificadas, claves públicas y personales no válidas, y muchos otros aspectos. Para encontrar estos problemas, es posible que también tengas que comprobar la configuración de pago.

## Aplicar una configuración coherente en Adobe Commerce y PayPal

Asegúrese de haber aplicado la misma configuración y de haber habilitado las mismas funcionalidades en la configuración de la cuenta de Commerce Admin y de PayPal.

### Ejemplo de problema de configuración

Al aplicar la solución PayPal Express Checkout, las transacciones basadas en respuestas de AVS/CSC deben rechazarse en **PayPal Manager** (Configuración del servicio > Configuración > Opciones de seguridad) y en **Commerce Admin** ( **Tiendas** > Configuración > **Ventas** > **Métodos de pago** ...).
![magento_paypal_settings_2.4.1.png](assets/magento_paypal_settings_2.4.1.png)
Para obtener más información, consulta la siguiente documentación: [PayPal](https://www.paypalobjects.com/en_US/vhelp/paypalmanager_help/setup.htm) y [Adobe Commerce](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html) en nuestra guía de usuario.

## Permitir transacciones de referencia

Si el método de pago de PayPal incluye API con acuerdos de facturación y transacciones de referencia, asegúrese de que estén activados y configurados correctamente en la configuración.

### Solución de problemas adicional

Consulte los siguientes artículos:

* [Solicitud rechazada de puerta de enlace de PayPal - problema de factura duplicada](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26838) en nuestra base de conocimiento de soporte.
* [Cambiar el id. de incremento para la nueva entidad de almacén](/help/how-to/general/change-increment-id-for-a-db-entity-order-invoice-credit-memo-etc-on-particular-store.md) en nuestra base de conocimiento de soporte.

## Póngase en contacto con el soporte técnico para recopilar registros de pago avanzados

Para solucionar problemas de pago complicados, el Equipo de Soporte de Adobe Commerce puede pedirle que aplique un parche específico para habilitar el registro de pagos avanzado. En este caso, los pasos deben ser los siguientes:

[Enviar un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) con los siguientes detalles:

* Especifique el problema con tantos detalles como sea posible.
* Enumere los pasos que ha intentado seguir con este artículo, base de conocimientos y otros recursos. Incluir todos los resultados.
* Solicite un parche del registro de pagos avanzados (número de referencia MDVA-4352) e instrucciones para aplicar el parche.

Si recibe el parche de Registro de pagos avanzados:

* Aplique el parche.
* Recopile registros y adjúntelos a su [ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
* Espere a recibir más recomendaciones del equipo de soporte de Adobe Commerce.
