---
title: Error al realizar el pedido con la cuenta de espacio aislado de Authorize.net (se produjo un error en el servidor)
description: Este artículo proporciona una corrección para el mensaje de error "*Se ha producido un error en el servidor*" al realizar un pedido con Authorize.Net Direct Post.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Error al realizar el pedido con la cuenta de espacio aislado de Authorize.net (se produjo un error en el servidor)

Este artículo proporciona una corrección para el mensaje de error &quot;*Se produjo un error en el servidor*&quot; al realizar un pedido mediante la publicación directa de Authorize.Net.

>[!WARNING]
>
>**Aviso de obsolescencia**
>
>Debido a la Directiva de servicios de pago [PSD 2](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive) y a la continua evolución de muchas API, Authorize.Net corre el riesgo de quedar obsoleto y dejar de ser compatible con la seguridad en el futuro. Por este motivo, ahora está en desuso y le recomendamos que lo deshabilite en la configuración de Adobe Commerce y que realice la transición a la [extensión de Commerce Marketplace](https://marketplace.magento.com/extensions.html) correspondiente.
>
>**Esta integración se ha eliminado de la versión 2.4.0 de Adobe Commerce y ha quedado obsoleta de las versiones actuales de 2.3.**
>
>Para obtener más información sobre cómo realizar una transición segura de las integraciones de pago obsoletas, consulta nuestro [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problema

Realizar un pedido con la cuenta de espacio aislado [Authorize.Net Direct Post](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/error-placing-order-with-authorize-net-sandbox-account-an-error-occurred-on-the-server) provoca un mensaje de error:

>>
&quot;Se ha producido un error en el servidor. Intente realizar el pedido de nuevo&quot;

## Causa 1: el modo de prueba está habilitado

No parece obvio, pero la configuración de **Modo de prueba** de Authorize.net debe establecerse en **No** incluso al realizar pruebas con la cuenta de espacio aislado.

## Solución 1: deshabilitar el modo de prueba

1. Vaya a **Tiendas** > **Configuración** > **Ventas** > **Métodos de pago** > **Otros métodos de pago** > **Authorize.net Direct Post**.
1. Establezca **Modo de prueba** en &quot;No&quot; (desmarque **Usar valor del sistema** y, a continuación, seleccione &quot;No&quot; en el menú).
1. Haga clic en **Guardar configuración**.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Causa 2: direcciones URL incorrectas

La configuración de Authorize.net puede contener direcciones URL incorrectas para los recursos esenciales de Authorize.Net.

## Solución 2: proporcione las direcciones URL correctas

* **URL de puerta de enlace:**   `https://test.authorize.net/gateway/transact.dll`
* **URL de detalles de transacción:**   `https://apitest.authorize.net/xml/v1/request.api`
* **Referencia de API:**   `https://developer.authorize.net/api/reference/`

## Si nada ayudó: obtener información de depuración

Si al realizar un pedido con Authorize.net se produce un error con un elemento no informativo *&quot;Se produjo un error&quot;*, compruebe el Adobe Commerce `debug.log`.

### Transact.dll

En caso de que `debug.log` esté vacío, compruebe la respuesta de **transact.dll** en la consola del explorador web:

1. Abra la consola.
1. Antes de hacer un pedido, ve a la pestaña **Red** y selecciona **Conservar registro**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtre las respuestas por **transact.dll** para ver un mensaje de respuesta con un posible error.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
