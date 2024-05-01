---
title: Actividad de tarjeta activa de PayPal Payflow Pro
description: ACTUALIZADO el 2 de abril de 2019
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# Actividad de tarjeta activa de PayPal Payflow Pro

ACTUALIZADO el 2 de abril de 2019

La integración PayPal Payflow Pro en Adobe Commerce está siendo activamente objetivo de la actividad de tarjeta, donde los atacantes intentan realizar cientos de transacciones de $0 con tarjetas de crédito robadas para comprobar la validez de la tarjeta.

Actualmente, la actividad se dirige a las versiones de esta integración de Payflow Pro que se incluyeron en Adobe Commerce 2.1.x, 2.2.x, 2.3.x para Magento Open Source y Commerce (local y en la nube). La actividad de tarjeta es inherente a la forma en que Payflow Pro está integrado en los carros de compras.

>[!NOTE]
>
>Para ayudar a resolver estos problemas, hemos proporcionado nuevos paquetes de Composer para agregar Google reCAPTCHA o CAPTCHA al formulario de cierre de compra de Payflow Pro. Se recomienda instalar estos paquetes en todas las versiones y ediciones de Adobe Commerce.

El problema afecta a las siguientes versiones de Adobe Commerce:

* Adobe Commerce local v2.1.x, 2.2.x, 2.3.x
* Adobe Commerce en infraestructura en la nube v2.1.x, 2.2.x, 2.3.x

## Problema

Los síntomas de estas crisis incluyen:

* Tu cuenta PayPal Payflow Pro muestra cientos de transacciones fraudulentas identificadas
* PayPal puede suspender una cuenta de Payflow Pro debido a las transacciones fraudulentas entrantes y cobrar cargos sustanciales

## Solución

Para ayudar a protegerse de estos ataques, le recomendamos añadir Google reCAPTCHA (recomendado) o CAPTCHA al formulario de pago y envío de Payflow Pro. Esto incluye la instalación de los paquetes de Composer y la configuración de Google reCAPTCHA o CAPTCHA en el Administrador de Commerce.

### Paquetes de instalación

Adobe ha creado dos opciones de paquete para añadir Google reCAPTCHA o CAPTCHA al formulario de cierre de compra de Payflow Pro. La instalación de uno de estos paquetes actualizará las instalaciones actuales y añadirá una opción que puede ayudar a mejorar esta seguridad al formulario de pago y envío de Payflow Pro.

Estos paquetes son compatibles con las siguientes implementaciones y versiones de Adobe Commerce:

Adobe Commerce (todos los métodos de implementación) y Magento Open Source 2.1.x, 2.2.x, 2.3.x

La instalación requiere comandos CLI para la instancia de Adobe Commerce. Puede que se requiera asistencia de desarrollador.

>[!NOTE]
>
>Se recomienda instalar y configurar Google reCAPTCHA además de instalar las actualizaciones relevantes del formulario de cierre de compra de Payflow Pro. Esta opción proporciona una comprobación invisible y varias opciones de configuración.

#### Instalación de Google reCAPTCHA y actualizaciones del formulario de cierre de compra

El `magento/module-paypal-recaptcha` El paquete contiene actualizaciones del formulario de pago de integración con Google reCAPTCHA y Payflow Pro. Incluso si tiene el módulo reCAPTCHA instalado y configurado, le recomendamos que instale este paquete.

Ejecute los siguientes comandos para instalarlo.

**Para Adobe Commerce local:**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Para Adobe Commerce en la infraestructura en la nube:**

1. Ejecute el siguiente comando:

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. Confirmar y enviar cambios:

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. Espere a que se complete la implementación.

#### Instalar actualizaciones de formularios de cierre de compra para CAPTCHA

El `magento/module-paypal-captcha` contiene la integración con el módulo nativo CAPTCHA de Adobe Commerce.

Ejecute los siguientes comandos para instalarlo:

**Para Adobe Commerce local:**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Para Adobe Commerce en la infraestructura en la nube:**

1. Ejecute el siguiente comando:

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. Confirmar y enviar cambios:

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. Espere a que se complete la implementación.

### Configuración de Google reCAPTCHA o CAPTCHA

Una vez instalado el paquete, configure Google reCAPTCHA (recomendado) o CAPTCHA como se describe en los siguientes documentos:

* [Google reCAPTCHA](https://docs.magento.com/user-guide/stores/security-google-recaptcha.html) en nuestra guía del usuario.
* [CAPTCHA](https://docs.magento.com/user-guide/stores/security-captcha.html) en nuestra guía del usuario.

La nueva opción del formulario de cierre de compra es:

* Google reCAPTCHA: Utilizar en el formulario de pago PayPal Payflow Pro
* CAPTCHA: Payflow Pro

## Asistencia y contactos de PayPal

Póngase en contacto con el servicio de asistencia al comerciante de PayPal Payflow para obtener más información sobre los servicios de protección contra el fraude. Puedes solicitar al equipo de Soporte de PayPal que habilite [Servicios básicos de protección contra el fraude](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/) filtros para proporcionar el control más estricto posible sobre los pagos, de modo que pueda denegar automáticamente los pagos que puedan dar lugar a transacciones fraudulentas y aceptar pagos que no suelen ser un problema. Tenga en cuenta que una vez que active los filtros de los Servicios de protección contra el fraude de PayPal, las transacciones pueden tardar hasta dos horas en liquidarse.

>[!NOTE]
>
>Para obtener más información, consulte KB de PayPal [&quot;Adobe se ha puesto en contacto conmigo acerca de mi integración con Payflow Pro. ¿Qué tengo que hacer?&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**Detalles de asistencia de PayPal Payflow Merchant**

El horario laboral de Payflow Merchant Support es de lunes a viernes de 7:00 AM a 8:00 PM CST. Puede ponerse en contacto con el servicio de asistencia al comerciante de Payflow para obtener ayuda por teléfono o correo electrónico:

* Teléfono: 1-888-883-9770 (Seleccionar petición 2)
* Clientes internacionales: 1-408-967-0191
* Correo electrónico: [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

Soporte para Australia

* Lunes a viernes de 8:00 a.m. a 7:00 p.m. (hora de Australia)
* Teléfono: +61 2 8288 0198
* Correo electrónico: [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
