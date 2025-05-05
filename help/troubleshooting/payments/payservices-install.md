---
title: Solucionar problemas de instalación de Payment Services
description: Este artículo explica los errores que puede experimentar al instalar Payment Services y proporciona soluciones para corregirlos de modo que pueda completar la instalación.
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Solucionar problemas de instalación de Payment Services

Este artículo explica los errores que puede experimentar al instalar Payment Services y proporciona soluciones para corregirlos de modo que pueda completar la instalación.

## Productos y versiones afectados

* [Servicios de pago](https://marketplace.magento.com/magento-payment-services.html) ahora es compatible con las versiones 2.4.0 a 2.4.4 de Adobe Commerce.

## Problema - Claves de composición incorrectas

Al instalar la extensión de servicios de pago, puede que aparezca un mensaje de error que indica que ha utilizado claves de Compositor incorrectas durante la instalación.

<u>Pasos a seguir</u>:

1. Intento de [instalar Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=es).
1. Consulte el siguiente error:

   *No se encontró una versión coincidente del paquete magento/payment-services. Compruebe la ortografía del paquete, la restricción de versión y que el paquete está disponible en una estabilidad que coincida con su estabilidad mínima (estable).*

<u>Resultado esperado</u>:

Puede seguir estas [instrucciones de instalación](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=es) en nuestra documentación para desarrolladores para instalar correctamente Payment Services.

<u>Resultado real</u>:

Durante la instalación, verá un mensaje de error que indica que no ha utilizado las claves del Compositor correctas durante la instalación.

### Causa

Durante la instalación se han utilizado claves de composición incorrectas.

### Solución

Compruebe que [sus claves de Compositor están vinculadas al identificador de Magento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=es#incorrect-composer-keys) utilizado durante el registro de Servicios de pago.

## Problema: uso del mismo espacio de datos en varias instancias

Ejecución de una configuración de varios entornos con servicios de pago en cada uno.

### Solución

La misma clave de API se puede utilizar en todas las instancias, pero cada instancia necesita utilizar su propio espacio de datos de SaaS.

Al crear un proyecto de SaaS, Commerce genera uno o más espacios de datos de SaaS en función de la licencia de Commerce:

* Adobe Commerce: un espacio de datos de producción, dos espacios de datos de prueba
* Magento Open Source: un espacio de datos de producción, sin espacios de datos de prueba

Siga las instrucciones de la [clave de API de Commerce y clave privada](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html?lang=es#obtain-api-credentials) para configurar correctamente la extensión de servicios de pago.

## Problema - No hay suficiente memoria para PHP

Al instalar la extensión de servicios de pago, puede que vea un mensaje de error que indica que no tiene suficiente memoria para PHP.

<u>Pasos a seguir</u>:

1. Intento de [instalar Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=es).
1. Consulte el siguiente error o similar:

   *Error grave: se agotó el tamaño de memoria permitido de 2146435072 bytes (se intentó asignar 4096 bytes) en phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php en la línea 52*

<u>Resultado esperado</u>:

Puede seguir estas [instrucciones de instalación](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=es) en nuestra documentación para desarrolladores para instalar correctamente Payment Services.

<u>Resultado real</u>:

Durante la instalación, verá un mensaje de error que indica que no tiene suficiente memoria para PHP.

### Causa

El límite para PHP en su entorno no está establecido en un umbral lo suficientemente alto.

### Solución

[Aumente el límite de memoria para PHP](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=es#not-enough-memory-for-php) en su entorno en `php.ini`.
