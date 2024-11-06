---
title: Falta el archivo CSV de productos exportados en la columna de estado de Adobe Commerce
description: Este artículo proporciona una solución al problema cuando no puede localizar la columna de estado en el archivo CSV que contiene los productos exportados.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Falta el archivo CSV de productos exportados en la columna de estado de Adobe Commerce

Este artículo proporciona una solución al problema cuando no puede localizar la columna de estado (es decir, indicando si el producto está habilitado o deshabilitado) en el archivo CSV que contiene los productos exportados. El estado del producto se indica mediante la columna [!UICONTROL product_online].

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) [todas las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

No puede encontrar la columna [!UICONTROL status] en el archivo CSV que contiene los productos exportados. Por lo tanto, por ejemplo, exporta un CSV de todos los SKU, con su estado, pero la tabla parece no tener la columna [!UICONTROL status].

<u>Pasos a seguir:</u>

1. En el Administrador de Adobe Commerce, seleccione **[!UICONTROL System]**, en **[!UICONTROL Data Transfer]** seleccione **[!UICONTROL Export]**.
1. En la sección **[!UICONTROL Export Settings]**, seleccione en la lista desplegable **[!UICONTROL Entity Type]** **[!UICONTROL Products]**.
1. Busque **[!UICONTROL status]**, que aparece en **[!UICONTROL Attribute Code]**. Verá ese código de atributo en la lista de atributos disponibles (**[!UICONTROL Enable Product]**).
1. Haga clic en **[!UICONTROL Export]**.

<u>Resultado esperado:</u>

En el archivo CSV que acaba de exportar, verá una columna denominada [!UICONTROL status].

<u>Resultado real:</u>

No ve una columna denominada [!UICONTROL status] en el archivo csv exportado.

## Causa

Se ha cambiado el nombre del atributo de estado del producto en el archivo CSV. Ahora es la columna [!UICONTROL product_online].

## Solución

1. Seleccione **[!UICONTROL System]**, en **[!UICONTROL Data Transfer]** seleccione **[!UICONTROL Import]**.
1. Haga clic en **[!UICONTROL Download Sample File]**.
1. Puede ver la columna [!UICONTROL product_online] en el archivo CSV.

## Lectura relacionada

* [Trabajando con archivos CSV](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-csv) en nuestra guía del usuario.
* [Referencia de atributos de exportación de productos](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-attributes-product) en nuestra guía del usuario.
