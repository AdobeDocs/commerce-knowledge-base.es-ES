---
title: El administrador no puede crear un pedido/repedido cuando el pago del Braintree está activado
description: Este artículo proporciona un parche para el problema de Adobe Commerce 2.4.5 en el que un usuario administrador no puede crear pedidos ni volver a pedidos de clientes cuando el método de pago del Braintree está habilitado.
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# El administrador no puede crear un pedido/repedido cuando el pago del Braintree está activado

Este artículo proporciona un parche para el problema de Adobe Commerce 2.4.5 en el que un usuario administrador no puede crear pedidos ni volver a pedidos de clientes cuando el método de pago del Braintree está habilitado.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.4.5
* Adobe Commerce local 2.4.5
* Magento Open Source 2.4.5

## Problema

<u>Pasos a seguir</u>:

1. Se usa la integración del Braintree principal (**Tiendas** > **Configuraciones** > **Ventas** > **Método de pago** > **Braintree**).
1. Con Tienda Luma, realice un pedido.
1. Vaya a la IU de administración > **Ventas**.
1. Intente crear un nuevo pedido para un cliente o vaya a un pedido realizado anteriormente y haga clic en **Reordenar**.

<u>Resultado esperado</u>:

Los usuarios administradores pueden crear correctamente pedidos y repedidos para los clientes cuando el método de pago del Braintree está activado.

<u>Resultado real</u>:

Los usuarios administradores no pueden crear pedidos ni repedidos para clientes cuando el método de pago del Braintree está activado y devuelve el siguiente error:

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## Causa

Dependencias de clase incorrectas (`vendor/paypal/module-braintree-core/Block/Form.php`)

## Solución

Aplique el parche proporcionado en este artículo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, haga clic en el siguiente vínculo:

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>Además, para Adobe Commerce en comerciantes de infraestructura en la nube: Adobe ha incluido la corrección en los parches de la nube para Commerce versión 1.0.18. Consulte [Parches de nube para las notas de la versión de Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html) en nuestra documentación para desarrolladores para obtener instrucciones sobre cómo aplicar el paquete más reciente.

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce en infraestructura en la nube 2.4.5
* Adobe Commerce local 2.4.5
* Magento Open Source 2.4.5

>[!NOTE]
>
>El parche no es compatible con ninguna otra versión ni edición de Adobe Commerce ni de Magento Open Source.

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte técnico para obtener instrucciones detalladas.
