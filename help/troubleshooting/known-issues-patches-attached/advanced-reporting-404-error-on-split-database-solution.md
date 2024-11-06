---
title: Error de Advanced Reporting 404 en la solución de base de datos dividida
description: Este artículo proporciona un parche para los usuarios de Adobe Commerce 2.3.x con la [solución de base de datos dividida](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master) que experimentan un error 404 al intentar utilizar la creación de informes avanzada.
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Error de Advanced Reporting 404 en la solución de base de datos dividida

Este artículo proporciona un parche para los usuarios de Adobe Commerce 2.3.x con la [solución de base de datos dividida](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master) que experimentan un error 404 al intentar usar el sistema de informes avanzado.

## Productos y versiones afectados

Adobe Commerce 2.3.0 - 2.3.5-p1

## Problema

El parche corrige el problema en el que se utiliza un nombre de conexión incorrecto para recopilar datos de presupuestos. Debido a que se utiliza un nombre de conexión incorrecto, los datos de presupuesto no se envían al Magento Business Intelligence (MBI) y no se pueden generar los informes.

## Solución

Aplique el [parche](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip) proporcionado en este artículo.

## Parche

El parche se adjunta a este artículo. Para descargarlo, haga clic en el siguiente vínculo:

[MDVA-26831\_EE\_2.3.4\_v1.composer.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## Cómo aplicar el parche

Descomprima el archivo y siga las instrucciones de [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
