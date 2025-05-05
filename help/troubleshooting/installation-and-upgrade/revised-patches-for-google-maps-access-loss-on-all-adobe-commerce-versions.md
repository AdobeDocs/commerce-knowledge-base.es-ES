---
title: Revisiones revisadas para la pérdida de acceso a Google Maps en todas las versiones de Adobe Commerce
description: 'Este artículo proporciona una corrección para los comerciantes de Adobe Commerce que no son compatibles con ninguna de las  [!DNL Google Maps] versiones recientes a partir de la versión 3.54+.'
feature: Install, Upgrade
role: Developer
source-git-commit: cf235c2fdd7a36d7e3b126de35c51e6711cd3845
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Revisiones para [!DNL Google Maps] pérdida de acceso en todas las versiones de Adobe Commerce

Este artículo proporciona una corrección para comerciantes de Adobe Commerce que no son compatibles con ninguna versión reciente de [!DNL Google Maps] a partir de la versión 3.54 o posterior. Esta corrección sirve para resolver el problema en el cual los comerciantes de Adobe Commerce ya no tienen acceso a [!DNL Google Maps] en ninguna versión de Adobe Commerce.

## Versiones y productos afectados

* Versiones de Adobe Commerce y otras tecnologías utilizadas.
* Adobe Commerce *2.4.4* - *2.4.7* en la nube y versiones locales.

## Problema

El *14 de junio de 2024* [!DNL Google Maps], versión *3.53* llegó al final de su vida útil y fue desactivada por [!DNL Google].

Para obtener más información, consulte [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce no era compatible con ninguna versión de [!DNL &#x200B; Google Maps] reciente de la versión 3.54 o posterior.

La incompatibilidad se debe a la heredada `prototype.js script`, que se cargó a través de `lib/web/legacy-build.min.js` e invalida la función Array.from nativa, lo que provoca un conflicto directo con la API [!DNL &#x200B; Google Maps].

Consulte [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Pasos a seguir</u> :

1. Haga clic en **[!UICONTROL Content]** > **[!UICONTROL Pages]** > y seleccione un **[!UICONTROL New Page]**.
1. Expanda el bloque de contenido y haga clic en el botón Editar **[!DNL PageBuilder]**.
1. Arrastre el bloque de contenido de mapa del menú **[!DNL PageBuilder]** a la página.

<u>Resultado esperado:</u>

[!DNL Google Maps] debe funcionar según lo esperado.

<u> Resultado real:</u>

Al soltar el bloque de contenido de mapa del menú **[!DNL PageBuilder]** en la página, aparece un mensaje de error como *&quot;Lo sentimos. Se produjo un error&quot;* se muestra.

## Solución

* Todos los comerciantes de cualquier versión de parche 2.4.4, 2.4.5, 2.4.6 o 2.4.7 deben aplicar estos parches correspondientes a su versión.

## Parche

Utilice los siguientes parches adjuntos, según la versión de Adobe Commerce:

**Para las versiones 2.4.4:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Para las versiones 2.4.5:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Para las versiones 2.4.6:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Para las versiones 2.4.7:**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**Tenga en cuenta**

Este problema se solucionará de forma permanente en el ámbito de las versiones de parches de solo seguridad de agosto:
2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Lectura relacionada

[Cómo aplicar un parche del compositor proporcionado por el Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)