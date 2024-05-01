---
title: '''[!UICONTROL Recommendations] [!DNL JS] errores tras la actualización a la versión 2.4.5 de Adobe Commerce"'
description: Este artículo proporciona una corrección para los casos en los que después de la actualización a Adobe Commerce (todos los métodos de implementación), haya [!DNL JS] errores en la consola relacionados con el producto [!UICONTROL Recommendations] módulos.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] errores tras la actualización a la versión 2.4.5 de Adobe Commerce

Este artículo proporciona una corrección para los casos en los que después de la actualización a Adobe Commerce (todos los métodos de implementación), haya [!DNL JS] errores en la consola relacionados con el producto [!UICONTROL Recommendations] módulos/unidades.

Actualmente no hay planes para abordar este problema en versiones futuras.

## Versiones y productos afectados

* Adobe Commerce (todos los métodos de implementación) al actualizar a la versión 2.4.5

## Problema

El problema se debe a que la página web de la tienda sigue haciendo referencia a algún producto eliminado [!UICONTROL Recommendations] módulos/unidades (bloques o widgets) en su página de inicio [!DNL CMS].

<u>Pasos a seguir</u>:

1. Actualice a Adobe Commerce 2.4.5.
1. Acceda a la página web de la tienda.
1. Haga clic con el botón derecho del ratón y seleccione **Inspect** para abrir el inspector web en el explorador web.
1. Haga clic en **[!UICONTROL Console]** pestaña.
1. Revise la [!DNL JS] errores.

<u>Resultados esperados</u>:

Actualización correcta sin [!DNL JS] errores.

<u>Resultados reales</u>:

Varios tipos diferentes de [!DNL JS] los errores se muestran en la consola del explorador web.

## Solución

Como solución alternativa, puede revisar todas las [!UICONTROL Recommendations] las unidades que haya utilizado en la página y elimine todas las unidades eliminadas.
