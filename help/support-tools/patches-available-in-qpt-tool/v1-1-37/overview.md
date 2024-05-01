---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.37'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.37.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4ccdba38-8171-4cc4-b8ef-d2c53dec0b47
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.37

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.37.

QPT v1.1.37 incluye los siguientes parches:

1. **ACSD-52613**: corrige el problema en el que los cachés e índices se actualizan incluso cuando no se realizan actualizaciones en `Inventory_source` elementos por API de rest.
1. **ACSD-51884**: corrige el problema en el que la ruta de acceso a la caché de la imagen del producto se vuelve incorrecta después de ejecutar el comando de cambio de tamaño.
1. **ACSD-53628**: corrige el problema en el que el informe de pedidos de ventas CSV muestra caracteres especiales incorrectos.
1. **ACSD-49843**: soluciona el problema en el que el enlace de la descarga del producto no está disponible después de que el artículo pedido se haya facturado automáticamente mediante el método de pago en línea con el *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* configuración habilitada.
1. **ACSD-53148**: corrige el problema en el cual dos solicitudes paralelas en GraphQL para agregar el mismo producto configurable al carro de compras resultaban en dos elementos independientes en el carro de compras con el mismo SKU de producto.
1. **ACSD-47054**: corrige el problema en el que el reíndice de previsualización ejecuta el reíndice para todas las tiendas, lo que provoca lentitud.
1. **ACSD-52606**: corrige el problema donde el mensaje de error *Su pedido no está listo para recoger* cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574**: corrige el problema en el cual la imagen no se actualiza en el front-end después de reemplazarla por otra imagen con el mismo nombre.
1. **ACSD-53728**: corrige el problema en el que el indexador EAV del producto tarda más en completarse.
1. **ACSD-53979**: corrige el problema de JS que se produce en la página de inicio si el mensaje de bienvenida contiene una comilla simple.
1. **ACSD-52143**: corrige el problema en el que las opciones personalizadas se eliminan después de la importación del producto.
1. **ACSD-53750**: corrige el *Tubo roto o conexión cerrada* error durante procesos múltiples `catalog_product_price` reindexe.

Utilice el menú de la izquierda para navegar a una página específica del parche.
