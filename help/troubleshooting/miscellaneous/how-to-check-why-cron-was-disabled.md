---
title: Cómo comprobar por qué se deshabilitó  [!DNL cron]
description: Este artículo ofrece soluciones de resolución de problemas para problemas con cron en Adobe Commerce sobre productos de infraestructura en la nube.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Cómo comprobar por qué se deshabilitó [!DNL cron]

Este artículo ofrece soluciones de solución de problemas con [!DNL cron] en Adobe Commerce en productos de infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

## Los siguientes son síntomas de [!DNL cron] problemas:

Ha observado que su [!DNL cron] no se estaba ejecutando.
Por ejemplo: verá las líneas siguientes en el archivo `app/etc/env.php`:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Una matriz vacía significaría que [!DNL cron] está **habilitado**:

```'cron' =>
  array (
  ),
```

## Causas

Existen varias razones por las que [!DNL cron] no está activo actualmente:

1. Se deshabilitó [!DNL cron] debido a que faltaba la configuración de [!DNL OpCache].
1. El equipo de infraestructura deshabilitó su [!DNL cron] porque estaba causando que su sitio no funcionara correctamente o que se cayera.
1. [!DNL cron] no se volvió a habilitar debido a un error en la implementación.

Consulte una de las siguientes secciones para ver una solución al problema.

## Soluciones

### Solución para la configuración de [!DNL OpCache] que falta {#solution-missed-opcache-settings}

Ver [[!DNL Cron] detenido debido a una configuración incorrecta o a que falta [!DNL OpCache] configuración](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) en nuestra base de conocimiento de Commerce.

### Solución para deshabilitada por el equipo de infraestructura {#solution-disabled-by-infrastructure-team}

1. Compruebe los tickets de asistencia anteriores en los que el sitio estaba caído o no respondía.
1. A continuación, compruebe si el equipo de infraestructura ha indicado que lo ha desactivado.
1. Compruebe que ha solucionado los problemas/inquietudes que le ha planteado el equipo de Infraestructura.
1. Envíe una [solicitud de soporte técnico](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) si necesita más ayuda para solicitar que se vuelva a habilitar [!DNL cron] y que se explique cómo ha solucionado los problemas que indicó el equipo de infraestructura.

### Error de solución para implementación {#solution-deployment-failed}

Compruebe los registros de implementación:

* [Ver y administrar registros](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/test/log-locations) en nuestra Guía de infraestructura de Commerce en la nube.
* [Comprobando el registro de implementación si la IU de Cloud tiene *`log snipped`* error](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) en nuestra base de conocimiento de Commerce.

1. Si la implementación ha fallado durante el paso `setup:upgrade`, [!DNL cron] no se habrá vuelto a habilitar.
Por ejemplo: verá esta línea en el registro de implementación:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. De lo contrario, es posible que la implementación haya fallado durante alguna otra etapa. Compruebe el registro de implementación y asegúrese de que aparecen ambas líneas (ejemplo abajo). Si no ve ambas líneas similares a esta en el registro, significa que [!DNL cron] no se volvió a habilitar:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Envíe una [solicitud de asistencia](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) si necesita más ayuda.**
