---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.0.8"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.0.8.
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Información general de [!DNL Quality Patches Tool] (QPT) v1.0.8

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.0.8.

QPT v1.0.8 incluye los siguientes parches:

1. **MDVA-28357**: reemplaza el analizador estándar por un analizador personalizado con token de palabra clave para el campo SKU en el índice [!DNL ElasticSearch] para que las consultas de búsqueda con comodines funcionen con SKU que contengan un guion (&quot;-&quot;).
1. **MDVA-29954**: corrige el problema por el que los mensajes de correo electrónico *Nueva solicitud de registro de empresa* y *Se le ha vinculado a una empresa* se envían desde una dirección incorrecta.
1. **MDVA-30112**: corrige el problema en el cual si el número de pedidos excede el valor de *tamaño del grupo*, Adobe Commerce considera los pedidos con estado *pendiente* como incoherencias.
1. **MDVA-30963**: corrige el problema en el cual los resultados de filtrado de productos configurados para contener solo valores especificados para el ámbito *Todas las vistas de tiendas* en el administrador, incluyen productos con valores anulados en el nivel de vista de tienda.
1. GET **MDVA-31150**: corrige el problema en el que los saldos de tarjetas regalo y de crédito de tienda no se devuelven mediante la llamada a la API Rest de factura, cuando la factura se registró mediante la llamada a la API Rest y el pedido se pagó parcialmente mediante cuentas de tarjeta de regalo y crédito de tienda.
1. **MDVA-31242**: corrige el problema donde se muestra un signo de moneda incorrecto en la cuadrícula [!UICONTROL Credit Memo].
1. **MDVA-31295**: corrige el problema en el cual los puntos de recompensa no se calculan cuando se completa un pedido parcial y los artículos se gravan.

Utilice el menú de la izquierda para navegar a una página específica del parche.
