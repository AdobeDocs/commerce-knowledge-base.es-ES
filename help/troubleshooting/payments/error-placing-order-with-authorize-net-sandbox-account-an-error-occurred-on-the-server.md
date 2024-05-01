---
title: Error al realizar el pedido con la cuenta de espacio aislado de Authorize.net (se produjo un error en el servidor)
description: Este artículo proporciona una corrección para el mensaje de error "*Se ha producido un error en el servidor*" al realizar un pedido con Authorize.Net Direct Post.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Error al realizar el pedido con la cuenta de espacio aislado de Authorize.net (se produjo un error en el servidor)

Este artículo proporciona una corrección para &quot;*Error en el servidor*&quot; mensaje de error al realizar un pedido con Authorize.Net Direct Post.

>[!WARNING]
>
>**Aviso de desuso**
>
>Debido a la Directiva sobre servicios de pago [PSD 2](https://docs.magento.com/user-guide/v2.3/stores/compliance-payment-services-directive.html) y la continua evolución de muchas API, Authorize.Net corre el riesgo de quedar obsoleto y ya no es compatible con la seguridad en el futuro. Por este motivo, ahora está en desuso y le recomendamos que lo deshabilite en la configuración de Adobe Commerce y realice la transición a la correspondiente [Extensión de Commerce Marketplace](https://marketplace.magento.com/extensions.html).
>
>**Esta integración se ha eliminado de la versión 2.4.0 de Adobe Commerce y ha quedado obsoleta de las versiones actuales de 2.3.**
>
>Para obtener más información sobre cómo realizar una transición segura desde integraciones de pago obsoletas, consulte nuestra [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problema

Realización de un pedido utilizando [Authorize.Net Direct Post](https://docs.magento.com/user-guide/v2.3/payment/authorize-net-direct-post.html) La cuenta de zona protegida causa un mensaje de error:

>>
&quot;Se ha producido un error en el servidor. Intente realizar el pedido de nuevo&quot;

## Causa 1: el modo de prueba está habilitado

No parece obvio, pero el de Authorize.net **Modo de prueba** la configuración debe establecerse en **No** incluso al realizar pruebas con la cuenta de zona protegida.

## Solución 1: deshabilitar el modo de prueba

1. Ir a **Tiendas** > **Configuración** > **Ventas** > **Métodos de pago** > **Otros métodos de pago** > **Authorize.net Direct Post**.
1. Establecer **Modo de prueba** a &quot;No&quot; (desmarque **Usar valor del sistema**, luego seleccione &quot;No&quot; en el menú).
1. Clic **Guardar configuración**.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Causa 2: direcciones URL incorrectas

La configuración de Authorize.net puede contener direcciones URL incorrectas para los recursos esenciales de Authorize.Net.

## Solución 2: proporcione las direcciones URL correctas

* **URL de puerta de enlace:**   `https://test.authorize.net/gateway/transact.dll`
* **URL de detalles de transacción:**   `https://apitest.authorize.net/xml/v1/request.api`
* **Referencia de API:**   `https://developer.authorize.net/api/reference/`

## Si nada ayudó: obtener información de depuración

Si al realizar un pedido con Authorize.net se produce un error con un *&quot;Se ha producido un error&quot;* error, compruebe el Adobe Commerce `debug.log`.

### Transact.dll

En caso de que la `debug.log` está vacío, marque la **transact.dll** Respuesta de en la consola del explorador web:

1. Abra la consola.
1. Antes de realizar un pedido, vaya a la **Red** y seleccione **Conservar registro**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtrar respuestas por **transact.dll** para ver un mensaje de respuesta con un posible error.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
