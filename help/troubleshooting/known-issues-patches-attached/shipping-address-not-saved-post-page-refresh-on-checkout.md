---
title: Dirección de envío no guardada después de actualizar la página al cerrar la compra
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.3 en el que el formulario de dirección de envío ya rellenado del cliente volvía a estar en blanco después de actualizar la página del explorador al cerrar la compra de invitado. El problema se experimentaba cuando se habilitaba el carro de compras persistente.
exl-id: b757e4af-7b1a-41bc-8460-9a6858c7aa5e
feature: Checkout, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Dirección de envío no guardada después de actualizar la página al cerrar la compra

Este artículo proporciona un parche para el problema conocido de Adobe Commerce 2.2.3 en el que el formulario de dirección de envío ya rellenado del cliente volvía a estar en blanco después de actualizar la página del explorador al cerrar la compra de invitado. El problema se experimentaba cuando se habilitaba el carro de compras persistente.

## Problema

Los clientes pasan por el proceso de pago y rellenan todos los formularios, incluida la dirección de envío. Llegan a la sección de Revisión y pagos y vuelven a cargar la página. El formulario está vacío y deben volver a introducir la dirección de envío. La funcionalidad de carro de compras persistente está habilitada.

<u>Pasos a seguir</u> :

**Requisitos previos**: la funcionalidad de carro de compras persistente está habilitada. Compruebe si está habilitado en el Administrador, en **Tiendas** > **Configuración** > **Clientes** o **Tiendas** > **Configuración** > **Ventas,** según la versión de Adobe Commerce.

1. Ve a la tienda.
1. Agregar productos al carro de compras.
1. Continúe con el pago y envío como invitado.
1. Escribe tu dirección de envío, elige opciones de envío y continúa asegurando el pago.
1. Se le redirigirá a la sección Revisión y pagos del cierre de compra.
1. Compruebe que ve la dirección de envío en la sección Enviar a.
1. Actualice la página.

<u>Resultado esperado</u>:

Puede continuar con el cierre de compra y se guardarán todos los datos.

<u>Resultado real</u>:

La dirección de envío está vacía, debe volver a introducirla.

## Parche

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-9718\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-9718_EE_2.2.3_COMPOSER_v1.patch.zip)

### Versiones de Adobe Commerce compatibles

**El parche se ha creado para:**

* Adobe Commerce 2.2.3

**El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.1.13 - 2.1.18
* Adobe Commerce en infraestructura en la nube 2.2.0 - 2.2.5
* Adobe Commerce local 2.0.X
* Adobe Commerce local 2.1.X
* Adobe Commerce local 2.2.0: 2.2.2 y 2.2.4: 2.2.5

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Archivos adjuntos
