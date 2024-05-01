---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.42

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42 incluye los siguientes parches:

1. **ACSD-53658**: soluciona el problema donde *[!UICONTROL Recently Viewed]* los datos del producto no se actualizan correctamente en la vista de tienda.
1. **ACSD-54626**: corrige un problema que impedía crear una regla de pedido de compra nueva (`createPurchaseOrderApprovalRule`) con el `NUMBER_OF_SKUS` mediante GraphQL.
1. **ACSD-53845**: corrige el problema de tiempo de espera de conexión MySQL cuando `consumer max_messages` = 0.
1. **ACSD-54890**: soluciona el problema donde `aggregate_sales_report_bestsellers_data` causa errores de MySQL debido a `/tmp` el disco no tiene espacio.
1. **ACSD-55112**: corrige el problema en el que las variables *[!UICONTROL Submit review]* se puede hacer clic varias veces sin [!DNL Google reCAPTCHA v3] validación.
1. **ACSD-54264**: corrige el problema donde el mensaje de error *No se puede actualizar el atributo solicitado. ID de fila: store_id* aparece cuando un cliente intenta cerrar la compra con una oferta negociable de otra vista de tienda.
1. **ACSD-54418**: corrige el problema en el que una cantidad fija de descuento se aplica incorrectamente a cada producto secundario del paquete de precios dinámicos.
1. **ACSD-55238**: soluciona el problema de guardar la metadescripción vacía del producto.
1. **ACSD-54966**: corrige el problema en el que un código de cupón con un uso limitado por cliente no se puede reutilizar si falla el pedido anterior.
1. **ACSD-54060**: corrige un problema en el cual un administrador restringido no puede guardar un producto si es hijo de otro producto asignado a un ámbito diferente.
1. **ACSD-48910**: corrige el problema en el que un producto agrupado asignado a varios orígenes se queda sin existencias después de que se factura y envía un pedido, incluso si tiene una cantidad distinta de cero.
1. **ACSD-55381**: corrige un error interno del servidor al realizar la consulta `configurable_product_option_uid` y `configurable_product_option_value_uid` campos de un B2B *[!UICONTROL Requisition list]* mediante GraphQL.
1. **ACSD-55628**: corrige la carga de un archivo en el formulario de registro de la empresa y el reemplazo de un archivo para un atributo del cliente en la tienda.

Utilice el menú de la izquierda para navegar a una página específica del parche.
