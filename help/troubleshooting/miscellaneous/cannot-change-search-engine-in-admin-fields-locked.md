---
title: No se puede cambiar el motor de búsqueda en app/etc/env.php
description: Este artículo proporciona una solución al problema de que intenta cambiar el motor de búsqueda en el administrador de Commerce, pero los campos están bloqueados.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# No se puede cambiar el motor de búsqueda en `app/etc/env.php`

Este artículo proporciona una solución al problema en el que intenta eliminar la configuración del motor de búsqueda de `app/etc/env.php` , pero después de la reimplementación, la configuración vuelve a la configuración anterior o se cambia a [!DNL OpenSearch] de forma predeterminada.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Intente cambiar el motor de búsqueda en el Administrador de Commerce, pero los campos están bloqueados.

## Causa

La configuración del motor de búsqueda está bloqueada en `app/etc/env.php` o el motor de búsqueda se define explícitamente en la variable `.magento.env.yaml` archivo.

## Solución

1. Compruebe la `.magento.env.yaml` en la fase de implementación y vea si la variable `SEARCH_CONFIGURATION` se ha configurado la variable. Ejemplo:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. Es el  `SEARCH_CONFIGURATION` presente? Si no está presente, la configuración del motor de búsqueda está bloqueada en [!DNL OpenSearch] de forma predeterminada. Para cambiar la configuración, debe agregar la variable a `.magento.env.yaml` con el valor apropiado para el motor de búsqueda. Si la variable `SEARCH_CONFIGURATION` está presente y desea modificar el motor, sustituya el valor existente para el motor en `.magento.env.yaml`. Valores posibles/conocidos: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic], y [!DNL amasty_elastic_opensearch].
1. Vuelva a implementar la instancia.
1. El campo del motor de búsqueda en Admin permanecerá bloqueado, pero debería actualizarse con el valor especificado.

## Lectura relacionada

* [Campos bloqueados en el administrador de Commerce](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) en la Guía de Commerce sobre infraestructura en la nube.
