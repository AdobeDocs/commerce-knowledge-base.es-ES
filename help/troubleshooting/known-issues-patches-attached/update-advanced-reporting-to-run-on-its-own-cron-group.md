---
title: Actualice los informes avanzados para que se ejecuten en su propio grupo cron
description: Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.3.0 en el que los informes avanzados no muestran datos. Esto se debe a que el trabajo de informes avanzados "analytics_collect_data" no se ejecuta de acuerdo con la programación. Este artículo proporciona un parche que creará un grupo cron de informes avanzados llamado analytics.
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Actualice los informes avanzados para que se ejecuten en su propio grupo cron

Este artículo proporciona un parche para el problema conocido de Adobe Commerce en la infraestructura en la nube 2.3.0 en el que los informes avanzados no muestran datos. Esto se debe a que el trabajo de informes avanzados `analytics_collect_data` no se ejecuta de acuerdo con la programación. Este artículo proporciona una revisión que creará un grupo cron de informes avanzados `analytics`.

## Problema

No se cargan datos en el módulo Informes avanzados.

## Parche

El parche se adjunta a este artículo. El parche mueve las tareas de trabajo cron `analytics` del grupo predeterminado a `analytics`.

Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

Después de aplicar el parche, ejecute la siguiente consulta SQL. La consulta debe ejecutarse para cambiar los registros de la tabla `cron_schedule`.

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### Versiones de Adobe Commerce compatibles:

El parche se ha creado para

* Adobe Commerce en infraestructura en la nube 2.3.0

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce: 2.2.2-2.2.10, 2.3.0-2.3.2 y 2.3.2-p2 y 2.3.3, para Adobe Commerce local y Adobe Commerce en la infraestructura en la nube

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Archivos adjuntos
