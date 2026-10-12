---
title: Cambio de precio base que afecta al precio de catálogo compartido
description: 'Este artículo responde a la pregunta: si un producto de un catálogo compartido tiene un precio personalizado y el precio base del producto cambia (por ejemplo, después de una actualización programada), ¿qué precio se aplica en el catálogo compartido?'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%
---
# Cambio de precio base que afecta al precio de catálogo compartido

Este artículo responde a la pregunta: si un producto de un catálogo compartido tiene un precio personalizado y el precio base del producto cambia (por ejemplo, después de una actualización programada), ¿qué precio se aplica en el catálogo compartido?

## Con el precio personalizado establecido en Porcentaje, el precio del catálogo compartido también cambia

Si el precio personalizado de un producto de un catálogo compartido se ha establecido en Porcentaje, el precio del catálogo compartido del producto se actualiza implícitamente después de cambiar el precio base.

En otras palabras, cuando se actualiza el precio base (mediante una actualización normal o programada), el precio del catálogo compartido también cambia después de aplicar el descuento porcentual.

## Con el precio personalizado establecido en Fijo, el precio del catálogo compartido no cambia

Si el precio personalizado de un producto de un catálogo compartido se ha establecido en Fijo, el precio del catálogo compartido nunca cambia, independientemente de la forma en que actualicemos el precio base (mediante actualización programada, administrador de Adobe Commerce, API o importación).

## La tienda siempre muestra el precio más bajo disponible

Si el precio base del producto cambia y se vuelve menor que el precio del catálogo compartido correspondiente, la Tienda muestra el precio base como el precio más bajo disponible en el sistema.

## Lectura relacionada

[Establezca los precios y la estructura para un catálogo compartido](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html?lang=es) en nuestra guía del usuario.
