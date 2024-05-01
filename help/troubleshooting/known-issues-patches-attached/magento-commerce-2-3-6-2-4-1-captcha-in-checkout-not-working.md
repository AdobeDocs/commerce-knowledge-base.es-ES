---
title: El CAPTCHA de Adobe Commerce 2.3.6 y 2.4.1 en el cierre de compra no funciona
description: Este artículo proporciona un parche para el problema en el que la función CAPTCHA para pago y envío no funciona como se espera en la página Realizar pedido cuando se utilizan proveedores de pago de terceros como Paypal Express, Payflow Pro o CyberSource en Adobe Commerce.
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# El CAPTCHA de Adobe Commerce 2.3.6 y 2.4.1 en el cierre de compra no funciona

Este artículo proporciona un parche para el problema en el que la función CAPTCHA para pago y envío no funciona como se espera en la página Realizar pedido cuando se utilizan proveedores de pago de terceros como Paypal Express, Payflow Pro o CyberSource en Adobe Commerce.

Este problema conocido se menciona en la documentación para desarrolladores de:

<u>Para Adobe Commerce 2.3.6</u>:

* [Notas de la versión de Adobe Commerce 2.3.6: Problemas conocidos](https://devdocs.magento.com/guides/v2.3/release-notes/commerce-2-3-6.html#known-issues)
* [Notas de la versión de Magento Open Source 2.3.6: problemas conocidos](https://devdocs.magento.com/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u>Para Adobe Commerce 2.4.1</u>:

* [Notas de la versión de Adobe Commerce 2.4.1: Problemas conocidos](https://devdocs.magento.com/guides/v2.4/release-notes/commerce-2-4-1.html#known-issues)
* [Notas de la versión de Magento Open Source 2.4.1: Problemas conocidos](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-1.html#known-issues)

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.3.6 y 2.4.1
* Magento Open Source 2.3.6 y 2.4.1

## Problema

<u>Pasos a seguir</u>

1. Configura al menos uno de estos métodos de pago en Commerce: Paypal Express, Payflow Pro o CyberSource.
1. Ir a **Administración > Tiendas > Configuración > Clientes > Configuración del cliente > CAPTCHA** .
   * Establecer **Habilitar CAPTCHA en la tienda** = *Sí* .
   * Seleccionar en **Forms** : *Cierre de compra/Colocación de pedido* , *Iniciar sesión* , y *Contraseña olvidada* .
   * Establecer **Modo de visualización** = *Después del número de intentos de inicio de sesión* (para hacer que la **Número de intentos de inicio de sesión erróneos** configuración aparecerá).
   * Establecer **Número de intentos de inicio de sesión erróneos** = *0* (para hacer que captcha funcione todo el tiempo).
1. En el front-end, agregue un producto al carro de compras e intente realizar el cierre de compra.
1. En la página de información de pago, introduce captcha e intenta pagar con Paypal Express, Payflow Pro o CyberSource.

<u>Resultado esperado:</u>

La función CAPTCHA funciona según lo esperado.

<u>Resultado real:</u>

Se muestra el mensaje de error: *Proporcione el código CAPTCHA e inténtelo de nuevo.*

## Solución

Aplique uno de los parches siguientes en función de si utiliza Adobe Commerce local/Adobe Commerce en la infraestructura en la nube/Magento Open Source 2.3.6 o 2.4.1.

## Parches

Los parches se adjuntan a este artículo, disponibles para su descarga en ambos `.composer` y `.git` formatos.

Para descargar un parche, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en uno de los siguientes vínculos:

<u>Para Adobe Commerce local/Adobe Commerce en la infraestructura en la nube/Magento Open Source 2.3.6</u> :

* [parche del Compositor MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [parche de Git MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>Para Adobe Commerce local/Adobe Commerce en la infraestructura en la nube/Magento Open Source 2.4.1</u> :

* [parche del Compositor MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [parche de Git MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

Estos parches no son compatibles con ninguna otra versión y edición de Adobe Commerce o de Magento Open Source.

## Cómo aplicar el parche

<u>parche de Composer</u>

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte para instrucciones de composer patch.

<u>parche de Git</u>

Consulte documentación para desarrolladores [Aplicación de parches: parches personalizados](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) para obtener instrucciones sobre el parche de git para Adobe Commerce/Magento Open Source.
