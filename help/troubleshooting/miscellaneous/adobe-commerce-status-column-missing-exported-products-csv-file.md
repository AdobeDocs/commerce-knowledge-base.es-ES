---
title: Falta el archivo CSV de productos exportados en la columna de estado de Adobe Commerce
description: Este artículo proporciona una solución al problema cuando no puede localizar la columna de estado en el archivo CSV que contiene los productos exportados.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Falta el archivo CSV de productos exportados en la columna de estado de Adobe Commerce

Este artículo proporciona una solución al problema cuando no puede localizar la columna de estado (es decir, indicando si el producto está habilitado o deshabilitado) en el archivo CSV que contiene los productos exportados. El estado del producto se indica mediante la variable [!UICONTROL product_online] columna.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) todo [versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

No puede localizar el [!UICONTROL status] en el archivo CSV que contiene los productos exportados. Por lo tanto, por ejemplo, exporta un CSV de todos los SKU, con su estado, pero la tabla parece no tener el [!UICONTROL status] columna.

<u>Pasos a seguir:</u>

1. En el Administrador de Adobe Commerce, seleccione **[!UICONTROL System]**, en **[!UICONTROL Data Transfer]** select **[!UICONTROL Export]**.
1. En el **[!UICONTROL Export Settings]** , seleccione en la **[!UICONTROL Entity Type]** menú desplegable **[!UICONTROL Products]**.
1. Buscar por **[!UICONTROL status]**, enumeradas en **[!UICONTROL Attribute Code]**. Verá ese código de atributo en la lista de atributos disponibles (**[!UICONTROL Enable Product]**).
1. Haga clic en **[!UICONTROL Export]**.

<u>Resultado esperado:</u>

En el archivo CSV que acaba de exportar, verá una columna denominada [!UICONTROL status].

<u>Resultado real:</u>

No ve una columna etiquetada como [!UICONTROL status] en el archivo CSV exportado.

## Causa

Se ha cambiado el nombre del atributo de estado del producto en el archivo CSV. Ahora es el [!UICONTROL product_online] columna.

## Solución

1. Seleccionar **[!UICONTROL System]**, en **[!UICONTROL Data Transfer]** select **[!UICONTROL Import]**.
1. Clic **[!UICONTROL Download Sample File]**.
1. Se puede ver el [!UICONTROL product_online] en el archivo CSV.

## Lectura relacionada

* [Uso de archivos CSV](https://docs.magento.com/user-guide/system/data-csv.html) en nuestra guía del usuario.
* [Referencia de atributos de exportación de productos](https://docs.magento.com/user-guide/system/data-attributes-product.html) en nuestra guía del usuario.
