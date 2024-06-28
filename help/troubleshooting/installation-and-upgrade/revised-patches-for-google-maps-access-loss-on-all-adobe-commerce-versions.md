---
title: Revisiones revisadas para la pérdida de acceso a Google Maps en todas las versiones de Adobe Commerce
description: 'Este artículo proporciona una corrección para los comerciantes de Adobe Commerce que no son compatibles con ningún [!DNL Google Maps] versiones a partir de 3.54+.'
feature: Install, Upgrade
role: Developer
source-git-commit: 98581cc9c251976339406f80764715096321126b
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Parches revisados para [!DNL Google Maps] pérdida de acceso en todas las versiones de Adobe Commerce

Este artículo proporciona una corrección para los comerciantes de Adobe Commerce que no son compatibles con ningún [!DNL Google Maps] versiones a partir de 3.54+. Esta corrección sirve para resolver el problema de que los comerciantes de Adobe Commerce no tienen acceso a [!DNL Google Maps] en cualquier versión de Adobe Commerce.

## Versiones y productos afectados

* Versiones de Adobe Commerce y otras tecnologías utilizadas.
* Adobe Commerce *2.4.4* - *2.4.7* en la nube y en las versiones locales.

## Problema

Activado *14 de junio de 2024* [!DNL Google Maps] version *3,53* llegó al final de su vida útil y fue desactivado por [!DNL Google].

Para obtener más información, consulte [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce no era compatible con ningún [!DNL  Google Maps] versiones a partir de 3.54+.

La incompatibilidad se debe a una versión heredada `prototype.js script`, que se cargó mediante `lib/web/legacy-build.min.js` reemplaza la función Array.from nativa, que genera un conflicto directo con [!DNL  Google Maps] API.

Consulte [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Pasos a seguir</u> :

1. Haga clic en **[!UICONTROL Content]** > **[!UICONTROL Pages]** > y seleccione un **[!UICONTROL New Page]**.
1. Expanda el bloque de contenido y haga clic en el icono Editar **[!DNL PageBuilder]** botón.
1. Arrastre el bloque de contenido de mapa desde el **[!DNL PageBuilder]** de menú a página.

<u>Resultado esperado:</u>

[!DNL Google Maps] debería funcionar según lo esperado.

<u> Resultado real:</u>

Al soltar el bloque de contenido de mapa de **[!DNL PageBuilder]** a la página, un mensaje de error como el siguiente *&quot;¡Lo siento! Se ha producido un error&quot;* se muestra.

## Solución

* Todos los comerciantes de cualquier versión de parche 2.4.4, 2.4.5, 2.4.6 o 2.2.7 deben aplicar estos parches correspondientes a su versión.

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

Este problema se solucionará de forma permanente en el ámbito de las versiones de parches de solo seguridad de agosto: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Lectura relacionada

[Cómo aplicar un parche del compositor proporcionado por el Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)