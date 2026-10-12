---
title: '[!UICONTROL Recommendations] [!DNL JS] errores después de actualizar a la versión 2.4.5 de Adobe Commerce'
description: Este artículo proporciona una corrección para cuando después de la actualización a Adobe Commerce (todos los métodos de implementación), haya [!DNL JS] errores en la consola relacionados con los módulos del producto [!UICONTROL Recommendations].
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%
---
# [!UICONTROL Recommendations] [!DNL JS] errores después de actualizar a la versión 2.4.5 de Adobe Commerce

Este artículo proporciona una corrección para cuando después de la actualización a Adobe Commerce (todos los métodos de implementación), haya [!DNL JS] errores en la consola relacionados con el producto [!UICONTROL Recommendations] módulos/unidades.

Actualmente no hay planes para abordar este problema en versiones futuras.

## Versiones y productos afectados

* Adobe Commerce (todos los métodos de implementación) al actualizar a la versión 2.4.5

## Problema

El problema se debe a que la página web de la tienda sigue haciendo referencia a algunos módulos/unidades (bloques o widgets) del producto eliminado [!UICONTROL Recommendations] en su página de inicio [!DNL CMS].

<u>Pasos a seguir</u>:

1. Actualice a Adobe Commerce 2.4.5.
1. Acceda a la página web de la tienda.
1. Haga clic con el botón derecho del ratón y seleccione **Inspeccionar** para abrir el inspector web en el explorador web.
1. Haga clic en la ficha **[!UICONTROL Console]**.
1. Revisar los errores de [!DNL JS].

<u>Resultados esperados</u>:

Actualización correcta sin [!DNL JS] errores.

<u>Resultados reales</u>:

Se muestran varios tipos diferentes de errores de [!DNL JS] en la consola del explorador web.

## Solución

Como solución alternativa, puede revisar todas las [!UICONTROL Recommendations] unidades que ha utilizado en la página y eliminar las unidades eliminadas.
