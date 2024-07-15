---
title: Errores de implementación en los que no se encontraron parches
description: "Este artículo proporciona una solución al problema en el que se muestra un error. *No se encontraron los siguientes parches: MDVA-XXXXX, ACSD-XXXXX. Compruebe la disponibilidad del comando 'status' de estos parches para la versión actual del Magento*."
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Errores de implementación en los que no se encontraron parches

Este artículo proporciona una solución al problema que se produce al actualizar la instancia cuando falla la implementación y ve un error en los registros de implementación: *No se encontraron los siguientes parches: MDVA-XXXXX, ACSD-XXXXX. Compruebe la disponibilidad del comando &quot;status&quot; de estas revisiones para la versión actual del Magento*.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Problema

Se produjo un error al actualizar Adobe Commerce: *No se encontraron las siguientes revisiones*.

## Causa

Los parches aplicados anteriormente a sus versiones anteriores no son aplicables o ya no están disponibles para su nueva versión.

## Solución

1. Compruebe su archivo de `.magento.env.yaml` en la sección QUALITY_PATCH, por ejemplo:

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Busque los identificadores de los parches en las [Notas de la versión de parches de calidad](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) para comprobar si se pueden aplicar a la nueva versión de Adobe Commerce a la que está actualizando.
1. Si el parche no se aplica a la nueva versión de Adobe Commerce a la que desea actualizar, quite el identificador del parche del archivo `.magento.env.yaml`.
1. Una vez que haya revisado todos los ID de parche indicados por el error, inserte los cambios y vuelva a implementar.

## Lectura relacionada

* [Aplicar parches](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) en la Guía de infraestructura de Commerce en la nube.
