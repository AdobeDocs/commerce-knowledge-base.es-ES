---
title: '''[!DNL Live Search]'' es incorrecto el tablero y la clasificación de resultados de búsqueda'
description: Este artículo proporciona información de solución de problemas si los datos del  [!DNL Live Search] panel son incorrectos o si la clasificación de los resultados de búsqueda no es la esperada.
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: 4c1199c31f83d7c2aaf28e259d63473779bf2efe
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# El panel [!DNL Live Search] y la clasificación de resultados de búsqueda son incorrectos

Si nota que los datos mostrados en el panel [!DNL Live Search] son incorrectos, o si la [clasificación de los resultados de búsqueda](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) no es la esperada, vea lo siguiente por posibles motivos:

* Falta el campo `topLevelSku` del contexto de producto en `productView` eventos. Esto provoca conversiones vacías y otras métricas inesperadas.

* El evento `add-to-cart` no tiene el campo `productContext` establecido y rellenado.

* El tipo de entorno es incorrecto. Por ejemplo, si el entorno se establece en *[!UICONTROL Testing]* en lugar de en *[!UICONTROL Production]*. Consulte [Contexto de tienda](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md) para obtener más información.

* Falta el contexto de resultados de búsqueda en el evento [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
