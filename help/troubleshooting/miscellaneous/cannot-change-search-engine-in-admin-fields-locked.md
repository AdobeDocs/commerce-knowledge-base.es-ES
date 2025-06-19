---
title: No se puede cambiar el motor de búsqueda en app/etc/env.php
description: Este artículo proporciona una solución al problema de que intenta cambiar el motor de búsqueda en el administrador de Commerce, pero los campos están bloqueados.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# No se puede cambiar el motor de búsqueda en `app/etc/env.php`

Este artículo proporciona una solución al problema en el que intenta quitar la configuración del motor de búsqueda del archivo `app/etc/env.php`, pero después de la reimplementación, la configuración vuelve a la configuración anterior o se cambia a [!DNL OpenSearch] de forma predeterminada.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Intente cambiar el motor de búsqueda en el Administrador de Commerce, pero los campos están bloqueados.

## Causa

La configuración del motor de búsqueda está bloqueada en el archivo `app/etc/env.php` o el motor de búsqueda se ha definido explícitamente en el archivo `.magento.env.yaml`.

## Solución

1. Compruebe el archivo `.magento.env.yaml` en la fase de implementación y vea si la variable `SEARCH_CONFIGURATION` se ha configurado. Ejemplo:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. ¿Está presente la variable `SEARCH_CONFIGURATION`? Si no está presente, la configuración del motor de búsqueda está bloqueada a [!DNL OpenSearch] de manera predeterminada. Para cambiar la configuración, debe agregar la variable al archivo `.magento.env.yaml` con el valor apropiado para el motor de búsqueda. Si la variable `SEARCH_CONFIGURATION` está presente y desea modificar el motor, reemplace el valor existente para el motor en `.magento.env.yaml`. Valores posibles o conocidos: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic] y [!DNL amasty_elastic_opensearch].
1. Vuelva a implementar la instancia.
1. El campo del motor de búsqueda en Admin permanecerá bloqueado, pero debería actualizarse con el valor especificado.

## Lectura relacionada

* [Campos bloqueados (atenuados) en el administrador de Commerce](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-26879) en la Guía de infraestructura de Commerce en la nube.
