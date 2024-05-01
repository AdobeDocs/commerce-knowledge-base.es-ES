---
title: Datos del informe Servicios de pago aplazado
description: Este artículo explica por qué se pueden retrasar los datos de informes en Payment Services.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Datos del informe Servicios de pago aplazado

Este artículo explica por qué se pueden retrasar los datos de informes en Payment Services.

## Productos y versiones afectados

* [Servicios de pago](https://marketplace.magento.com/magento-payment-services.html) ahora es compatible con las versiones de Adobe Commerce 2.4.0 a 2.4.4.

## Problema

Es posible que los datos de informes de Servicios de pago, para los informes de estado de pagos de Pagos y Pedidos, no se sincronicen inmediatamente.

Después de facturar (capturar) un pedido o emitir una nota de abono para un pedido, por ejemplo, es posible que el estado del pedido no esté disponible de inmediato.

<u>Pasos a seguir</u>:

Requisitos previos: Se realiza un pedido utilizando la funcionalidad Servicios de pago.

1. Un pedido es [facturado](https://docs.magento.com/user-guide/sales/invoice-create.html) (o [cancelado](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) o [reembolsado mediante nota de crédito](https://docs.magento.com/user-guide/sales/credit-memos.html)) en el [Administrador](https://docs.magento.com/user-guide/stores/admin.html).
1. Acceda al informe Estado de Pago del Pedido para ver información sobre dicho pedido.
1. El estado se muestra como `AUTHORIZED`, que es el estado del pedido antes de la facturación u otra acción de pedido.

   Commerce no ha sincronizado los datos y los ha enviado a Payment Services, por lo que el informe aún no reconoce el nuevo estado del pedido.

>[!NOTE]
>
>Este es solo un caso de uso común. Puede haber otros casos de uso cuando una [acción de pedido](https://docs.magento.com/user-guide/sales/order-actions.html) ocurre y los datos no están disponibles inmediatamente en el informe aplicable.

<u>Resultado esperado</u>: Los datos del informe se rellenan inmediatamente después de que se produzca una acción en un pedido.

<u>Resultado real</u>: puede haber un retraso en los datos de informes visibles para las acciones de pedidos que se acaban de completar. Los informes de pago pueden tardar entre 24 y 48 horas. Los informes de estado de pago del pedido pueden retrasarse unas horas.

## Causa

Existen dos factores que afectan a este retraso en los datos visibles en el administrador:

* La frecuencia con la que decide sincronizar (exportar y mantener) los datos de Commerce mediante [configuración en el Administrador](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* Periodo de tiempo en el que PayPal publica datos de informes.

## Solución

Para informes de estado de pagos de pedidos:

1. Vaya a **Ventas** > **Servicios de pago**.
1. Clic **Estado de pago del pedido** para consultar la tabla de informes de estado de pagos de pedidos.
1. Forzar resincronización haciendo clic en **forzar sincronización** en la esquina superior derecha de la tabla de informes.
1. Debería ver el último cambio actualizado en la marca de tiempo y las nuevas transacciones cargadas en la tabla del informe.

Para los informes de pago de PayPal, el resultado esperado es un retraso de 24 a 48 horas debido a la dependencia del periodo de tiempo de publicación de datos de PayPal.
