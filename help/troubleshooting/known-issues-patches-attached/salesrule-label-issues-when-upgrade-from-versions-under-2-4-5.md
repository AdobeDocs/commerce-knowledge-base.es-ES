---
title: '[!UICONTROL salesRule] etiquetas con problemas al actualizar desde las versiones &lt; 2.4.5'
description: Aplique un parche para resolver los problemas de **[!UICONTROL salesRule]** al actualizar desde las versiones de Adobe Commerce &lt; 2.4.5.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** problemas de etiquetas al actualizar desde versiones &lt; 2.4.5

La funcionalidad de ensayo de etiquetas **[!UICONTROL salesRule]** se introdujo en Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). El cambio puede provocar problemas al actualizar desde Adobe Commerce &lt; 2.4.5 a cualquier versión >= 2.4.5. Después de la actualización, existe la posibilidad de que las etiquetas **[!UICONTROL salesRule]** no coincidan. Para solucionar el problema, se debe aplicar un parche justo después de la actualización a una versión más reciente de Adobe Commerce.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube &lt; 2.4.5

## Parche

Utilice el siguiente parche adjunto:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Cómo aplicar el parche

1. Siga los pasos de [Realizar una actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=es) en la guía de Commerce.
1. Aplicar el parche adjunto antes de la fase **[!UICONTROL Update metadata]**.
(También puede aplicar el parche una vez que haya completado la fase **[!UICONTROL Update metadata]**, pero tendrá que ejecutar `bin/magento setup:upgrade` de nuevo).
1. Continúe con el resto de los pasos de [Realizar una actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=es).
