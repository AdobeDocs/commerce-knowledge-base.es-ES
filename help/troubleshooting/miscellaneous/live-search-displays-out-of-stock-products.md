---
title: '''[!DNL Live Search] muestra productos sin existencias independientemente de la configuración del estado de las existencias en "administración"'
description: Este artículo proporciona información sobre el problema conocido en el que la página de lista de productos (PLP) muestra el error *No podemos encontrar productos que coincidan con la selección* mientras que la ventana emergente de búsqueda devuelve algunos elementos.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] muestra productos sin existencias independientemente de la configuración del estado de las existencias en administración

>[!IMPORTANT]
>
>Este problema se solucionó en [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). Para instalar la versión más reciente, consulte [Actualizando [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) en la guía del usuario.

Este artículo proporciona información sobre el problema conocido en el que la Página de lista de productos (PLP) muestra el *No podemos encontrar productos que coincidan con la selección* error mientras la ventana emergente de búsqueda devuelve algunos elementos.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.4.x

## Problema

[!DNL Live Search] muestra los resultados de búsqueda independientemente de la configuración del estado de las existencias en el Administrador de Adobe Commerce. Incluso cuando la variable **[!UICONTROL Display Out-of-Stock Products]** se establece en *No*, se muestran los productos. Esto provoca el error PLP *No podemos encontrar productos que coincidan con la selección*.

<u>Pasos a seguir</u>:

1. Cree una categoría y añada productos. (Ejemplo: Categoría = _Jeans_, Product1 = _Blue Jeans_, Product2 = _Black Jeans_)
1. Agotar todos los productos de la categoría.
1. Establecer **[!UICONTROL Display Out-of-Stock Products]** hasta *No*.
1. En la tienda, escriba *Jeans* en el campo de búsqueda.
1. Clic **[!UICONTROL View All]** en la ventana emergente.

<u>Resultado esperado</u>:

Verá el *No podemos encontrar productos que coincidan con la selección* en PLP y no se muestra ningún producto en la ventana emergente de búsqueda.

<u>Resultado real</u>:

Verá el *No podemos encontrar productos que coincidan con la selección* en PLP, y ambos productos se muestran en la ventana emergente de búsqueda.

## Solución

No hay ninguna solución para este problema en este momento. Nuestro [!DNL Live Search] El equipo de proporcionará pronto una configuración para [!DNL Live Search] para mostrar los productos correctamente.

## Lectura relacionada

[Instalar [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html) en nuestra guía del usuario.
