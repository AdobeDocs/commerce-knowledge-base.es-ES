---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.0.8'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.8.
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] Información general de (QPT) v1.0.8

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.8.

QPT v1.0.8 incluye los siguientes parches:

1. **MDVA-28357**: reemplaza el analizador estándar por un analizador personalizado con un token de palabra clave para el campo SKU en el [!DNL ElasticSearch] índice para hacer que las consultas de búsqueda con comodines funcionen con SKU que contengan un guion (&quot;-&quot;).
1. **MDVA-29954**: corrige el problema en el que las variables *Nueva solicitud de registro de empresa* y *Se le ha vinculado a una compañía* los correos electrónicos se envían desde una dirección incorrecta.
1. **MDVA-30112**: corrige el problema en el que si el número de pedidos supera el *del mismo tamaño* valor, Adobe Commerce considera los pedidos con *pendiente* estado como incoherencias.
1. **MDVA-30963**: corrige el problema en el que los resultados de filtrado de productos configurados para solo contienen los valores especificados para *Todas las vistas de tiendas* En el ámbito de administración, incluya productos con valores anulados en el nivel de vista de tienda.
1. **MDVA-31150** GET : corrige el problema en el que los saldos de crédito de tienda y de tarjeta regalo no se devuelven mediante la llamada a la API REST de factura, cuando la factura se registró mediante la llamada a la API REST y el pedido se pagó parcialmente mediante cuentas de crédito de tienda y de tarjeta regalo.
1. **MDVA-31242**: corrige el problema en el que se muestra un signo de moneda incorrecto en [!UICONTROL Credit Memo] rejilla.
1. **MDVA-31295**: corrige el problema en el que los puntos de recompensa no se calculan cuando se completa un pedido parcial y los artículos se gravan.

Utilice el menú de la izquierda para navegar a una página específica del parche.
