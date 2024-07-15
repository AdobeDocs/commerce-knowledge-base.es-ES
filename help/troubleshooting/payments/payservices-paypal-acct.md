---
title: Cuenta de zona protegida de PayPal no verificada
description: Este artículo explica por qué es posible que no se haya verificado su cuenta de zona protegida de PayPal para Servicios de pago, lo que le impide completar la incorporación a la zona protegida.
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Cuenta de zona protegida de PayPal no verificada

Este artículo explica por qué es posible que no se haya verificado su cuenta de zona protegida de PayPal para Servicios de pago, lo que le impide completar la incorporación a la zona protegida.

## Productos y versiones afectados

* [Servicios de pago](https://marketplace.magento.com/magento-payment-services.html) ahora es compatible con las versiones 2.4.0 a 2.4.4 de Adobe Commerce.

## Problema

Nuestra [documentación de incorporación](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) le indica que se registre en una cuenta de PayPal, inicie sesión en la cuenta de desarrolladores de PayPal y luego cree una cuenta de zona protegida. Si seleccionas crear una nueva cuenta durante la incorporación en la ventana emergente de incorporación de PayPal, PayPal no podrá verificar tu cuenta de zona protegida y no podrás completar la incorporación.

<u>Pasos a seguir</u>:

1. Usted [instala Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) y [configura sus servicios de Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Va a **Servicios de pago** en el administrador y [comienza la incorporación a la zona protegida](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. En la ventana emergente de incorporación de PayPal que aparece, creas una nueva cuenta comercial (en lugar de [iniciar sesión con una cuenta de zona protegida de PayPal creada anteriormente](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) durante la incorporación.
1. Has completado correctamente la incorporación a PayPal.
1. Verá una notificación en el administrador de que los pagos de su zona protegida están pendientes y que debe confirmar su dirección de correo electrónico con PayPal para completar la incorporación.

   No has recibido un correo electrónico de confirmación porque PayPal no ha podido verificar tu dirección de correo electrónico.

## Causa

PayPal no podrá verificar tu cuenta de zona protegida y no podrás finalizar la incorporación a la misma (lo que significa que no podrás aceptar pagos ni probar el modo de zona protegida) si creas tu cuenta de zona protegida antes de tu cuenta de PayPal.

## Solución

1. Usando una cuenta de zona protegida creada en el portal [PayPal Developer](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Haga clic en [restablecer zona protegida](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) y reinicie la incorporación a la zona protegida.
1. [Póngase en contacto con el equipo de atención al cliente](mailto:payment-services-support@adobe.com) si no puede solucionar los problemas de su cuenta para que pueda reanudar la incorporación y aceptar pagos.
