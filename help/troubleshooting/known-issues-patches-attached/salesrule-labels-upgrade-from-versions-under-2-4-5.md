---
title: '**[!UICONTROL salesRules]** problemas con las etiquetas al actualizar desde versiones < 2.4.5'
description: Aplicar un parche para hacer frente a la **[!UICONTROL salesRules]** al actualizar desde versiones de Adobe Commerce < 2.4.5.
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# **[!UICONTROL salesRules]** etiquetas problemas al actualizar desde versiones &lt; 2.4.5

El **[!UICONTROL salesRules]** la funcionalidad de ensayo de etiquetas se ha introducido en Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). El cambio puede provocar problemas al actualizar desde Adobe Commerce &lt; 2.4.5 a cualquier versión >= 2.4.5. Después de la actualización, existe la posibilidad de que **[!UICONTROL salesRules]** las etiquetas no coinciden. Para solucionar el problema, se debe aplicar un parche justo después de la actualización a una versión más reciente de Adobe Commerce.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube &lt; 2.4.5

## Parche

Utilice el siguiente parche adjunto:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Cómo aplicar el parche

1. Siga los pasos de [Realización de una actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) en la guía de Commerce.
1. Aplique el parche adjunto antes de la **[!UICONTROL Update metadata]** fase.
(También puede aplicar el parche después de completar el **[!UICONTROL Update metadata]** fase, pero entonces debe ejecutar `bin/magento setup:upgrade` una vez más).
1. Continúe con el resto de los pasos indicados en [Realización de una actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
