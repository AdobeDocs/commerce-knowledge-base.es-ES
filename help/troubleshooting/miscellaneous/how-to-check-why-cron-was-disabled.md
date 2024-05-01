---
title: Cómo comprobar el motivo [!DNL cron] se deshabilitó
description: Este artículo ofrece soluciones de resolución de problemas para problemas con cron en Adobe Commerce sobre productos de infraestructura en la nube.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Cómo comprobar el motivo [!DNL cron] se deshabilitó

Este artículo ofrece soluciones de resolución de problemas para problemas con [!DNL cron] en Adobe Commerce sobre productos de infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

## Los siguientes son síntomas de [!DNL cron] problemas:

Ha notado que su [!DNL cron] no estaba corriendo.
Por ejemplo: verá las siguientes líneas en la `app/etc/env.php` archivo:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Una matriz vacía significaría que la variable [!DNL cron] es **activado**:

```'cron' =>
  array (
  ),
```

## Causas

Existen varias razones por las que la variable [!DNL cron] no está activo actualmente:

1. El [!DNL cron] se deshabilitó debido a errores [!DNL OpCache] configuración.
1. El equipo de Infraestructura ha desactivado su [!DNL cron], porque hacía que el sitio no funcionara correctamente/no funcionara.
1. El [!DNL cron] no se ha vuelto a habilitar porque se ha producido un error en la implementación.

Consulte una de las siguientes secciones para ver una solución al problema.

## Soluciones

### Solución para errores [!DNL OpCache] configuración {#solution-missed-opcache-settings}

Consulte [[!DNL Cron] detenido debido a una configuración incorrecta o falta [!DNL OpCache] configuración](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) en nuestra base de conocimiento de Commerce.

### Solución para deshabilitada por el equipo de infraestructura {#solution-disabled-by-infrastructure-team}

1. Compruebe los tickets de asistencia anteriores en los que el sitio estaba caído o no respondía.
1. A continuación, compruebe si el equipo de infraestructura ha indicado que lo ha desactivado.
1. Compruebe que ha solucionado los problemas/inquietudes que le ha planteado el equipo de Infraestructura.
1. Enviar una [Solicitud de soporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) si necesita más ayuda para solicitar que se vuelva a habilitar el [!DNL cron] y explicar cómo ha abordado los problemas que indicó el equipo de Infraestructura.

### Error de solución para implementación {#solution-deployment-failed}

Compruebe los registros de implementación:

* [Visualización y administración de registros](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) en nuestra Guía de infraestructura en la nube de Commerce.
* [Comprobación del registro de implementación si la IU de Cloud *`log snipped`* error](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) en nuestra base de conocimiento de Commerce.

1. Si la implementación ha fallado durante la `setup:upgrade` step, la [!DNL cron] no se habrá vuelto a habilitar.
Por ejemplo: verá esta línea en el registro de implementación:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. De lo contrario, es posible que la implementación haya fallado durante alguna otra etapa. Compruebe el registro de implementación y asegúrese de que aparecen ambas líneas (ejemplo abajo). Si no ve ambas líneas similares a esta en el registro, significa que la variable [!DNL cron] no se ha vuelto a habilitar:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Enviar una [Solicitud de soporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) si necesita más ayuda.**
