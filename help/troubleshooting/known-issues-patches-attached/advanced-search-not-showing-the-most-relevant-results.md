---
title: La búsqueda avanzada no muestra los resultados más relevantes
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce, en el que la búsqueda avanzada no muestra primero los resultados más relevantes.
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# La búsqueda avanzada no muestra los resultados más relevantes

Este artículo proporciona un parche para el problema conocido de Adobe Commerce, en el que la búsqueda avanzada no muestra primero los resultados más relevantes.

## Versiones afectadas {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce (todas las opciones de implementación) 2.x.x
* Magento Open Source 2.x.x

## Problema {#Advancedsearchnotshowingmostrelevantresults-Description}

La función de búsqueda avanzada no devuelve primero los resultados más relevantes, como lo está haciendo la búsqueda rápida. El problema no depende del tipo de motor de búsqueda seleccionado.

<u>Pasos a seguir:</u>

1. En la tienda, ve a la búsqueda rápida y busca &quot;Chaqueta ajustada&quot;.
1. Atención &quot;Orion Two-Tone Fited Jacket&quot; es el primer resultado.
1. Vaya a la búsqueda avanzada y busque &quot;Chaqueta ajustada&quot; en el campo del nombre.

<u>Resultado esperado:</u>

El &quot;Orion Two-Tone Fited Jacket&quot; es el primer resultado al utilizar la búsqueda avanzada, como el resultado más relevante.

<u>Resultado real:</u>

El &quot;Orion Two-Tone Fited Jacket&quot; no es el primer resultado, aunque es el más relevante.

## Solución {#Advancedsearchnotshowingmostrelevantresults-Solution}

Para resolver el problema, aplique el parche adjunto a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-7256\_EE\_2.1.7\_v1.composer.patch](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

El parche agrega la implementación para ordenar por relevancia para los resultados de búsqueda avanzada como campo de clasificación predeterminado.

El parche es compatible con todas las versiones y ediciones afectadas.

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Archivos adjuntos
