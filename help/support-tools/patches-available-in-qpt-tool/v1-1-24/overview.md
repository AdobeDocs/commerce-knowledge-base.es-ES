---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.24'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.24.
exl-id: 7c296124-c9ae-4b7c-b711-fc39741cabe2
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] Información general de (QPT) v1.1.24

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.24.

QPT v1.1.24 incluye los siguientes parches:

1. **ACSD-45168**: corrige el problema en el cual las direcciones URL compatibles con SEO no se generan para los productos que tienen *url_key* atributos anulados en el nivel de vista de tienda.
1. **ACSD-46617**: corrige el problema en el que las variables **[!UICONTROL Continue to Checkout]** aparece en gris aunque el subtotal sea mayor que el configurado *Cantidad mínima del pedido*.
1. **ACSD-46770**: corrige el problema en el que los correos electrónicos de pedido de administrador se envían incluso cuando el *Confirmación de pedido por correo electrónico* está desmarcada.
1. **ACSD-46865**: corrige el problema en el que las variables [!UICONTROL Shipment and Credit Memo] la cuadrícula no se rellena cuando la indexación asíncrona está habilitada.
1. **ACSD-47004**: corrige el problema en el que el IVA no se aplica a una dirección de facturación sin ID de IVA.
1. **ACSD-47079**: corrige el problema en el que el estado de las existencias de los productos compuestos (paquete, agrupados y configurables) no se actualiza cuando el estado de las existencias de subproductos cambia a través del POST de API de REST /rest/V1/inventory/source-items.
1. **ACSD-47137**: mejora la velocidad de carga de la galería de imágenes cuando la carpeta pub/media es muy grande.
1. **ACSD-47336**: correcciones *Se ha producido un error.* error al descartar las notificaciones en el administrador de Commerce.
1. **ACSD-47559**: corrige el problema en el que el área Vista previa de plantilla de correo electrónico no está totalmente visible.
1. **ACSD-47803**: corrige el problema en el que las muestras de productos configurables sin existencias se muestran como disponibles.
1. **ACSD-47920**: corrige el problema en el cual los pedidos se pueden realizar mediante la API de REST como usuario invitado incluso cuando la variable *Permitir cierre de compra de invitado* está desactivado.
1. **ACSD-47955**: corrige el problema en el cual GraphQL no muestra correctamente el descuento del carro de compras.

Utilice el menú de la izquierda para navegar a una página específica del parche.
