---
title: '[!DNL Live Search] muestra productos sin existencias independientemente de la configuración de estado de existencias en el administrador'
description: Este artículo proporciona información sobre el problema conocido en el que la página de lista de productos (PLP) muestra el error *No podemos encontrar productos que coincidan con la selección* mientras que la ventana emergente de búsqueda devuelve algunos elementos.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] muestra productos sin existencias independientemente de la configuración de estado de las existencias en el administrador

>[!IMPORTANT]
>
>Este problema se corrigió en [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html?lang=es). Para instalar la versión más reciente, consulte [Actualizando [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=es#update) en la guía del usuario.

Este artículo proporciona información sobre el problema conocido en el que la página de lista de productos (PLP) muestra el error *No podemos encontrar productos que coincidan con la selección* mientras que la ventana emergente de búsqueda devuelve algunos elementos.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.4.x

## Problema

[!DNL Live Search] muestra los resultados de búsqueda independientemente de la configuración del estado de las existencias en el Administrador de Adobe Commerce. Incluso cuando **[!UICONTROL Display Out-of-Stock Products]** está establecido en *No*, se muestran los productos. Provoca el error de PLP *No se pueden encontrar productos que coincidan con la selección*.

<u>Pasos a seguir</u>:

1. Cree una categoría y añada productos. (Ejemplo: Categoría = _Jeans_, Producto1 = _Blue Jeans_, Producto2 = _Black Jeans_)
1. Agotar todos los productos de la categoría.
1. Establezca **[!UICONTROL Display Out-of-Stock Products]** en *No*.
1. En la tienda, ingresa *Jeans* en el campo de búsqueda.
1. Haga clic en **[!UICONTROL View All]** en la ventana emergente.

<u>Resultado esperado</u>:

Verá el mensaje *No podemos encontrar productos que coincidan con la selección* en PLP y no se mostrará ningún producto en la ventana emergente de búsqueda.

<u>Resultado real</u>:

Verá el mensaje *No podemos encontrar productos que coincidan con la selección* en PLP, y ambos productos se mostrarán en la ventana emergente de búsqueda.

## Solución

No hay ninguna solución para este problema en este momento. Nuestro equipo [!DNL Live Search] pronto proporcionará una configuración para configurar [!DNL Live Search] de modo que muestre los productos correctamente.

## Lectura relacionada

[Instalar [!DNL Live Search]](https://experienceleague.adobe.com/es/docs/commerce-merchant-services/live-search/install) en nuestra guía de usuario.
