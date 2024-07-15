---
title: Problemas de comprobación de preparación de Cron
description: '''Este artículo proporciona soluciones para problemas de preparación de cron. Los siguientes son síntomas de problemas crónicos:'
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Problemas de comprobación de preparación de Cron

Este artículo proporciona soluciones para problemas de preparación de cron. Los siguientes son síntomas de problemas crónicos:

* Se muestra un mensaje de error acerca de la configuración de PHP `$HTTP_RAW_POST_DATA` aunque esté configurada correctamente.
* La comprobación de disponibilidad de PHP no muestra la versión de PHP como se muestra en la siguiente figura:
  ![upgr-shoot-no-cron.png](assets/upgr-tshoot-no-cron.png)
* Se muestra el siguiente error en el Administrador de Commerce:
  ![comando-cron-not-running.png](assets/compman-cron-not-running.png)
Para ver el error, es posible que tengas que hacer clic en **Mensajes del sistema** en la parte superior de la ventana de la siguiente manera:
  ![compman_sys-messages.png](assets/compman_sys-messages.png)

## Compruebe el crontab existente {#check-your-existing-crontab}

En esta sección se explica cómo comprobar si cron se está ejecutando actualmente y si está configurado correctamente.

Para verificar si su crontab está configurado o no:

1. Inicie sesión en el servidor de Commerce como propietario del sistema de archivos [Magento](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) o cambie a él.
1. Vea si existe el siguiente archivo: `$ ls -al <magento_root>/var/.setup_cronjob_status`. Si el archivo existe, cron se ha ejecutado correctamente en el pasado. Si el archivo *no existe*, o bien aún no ha instalado Adobe Commerce o no se está ejecutando cron. En cualquier caso, continúe con el siguiente paso.
1. Obtenga más información sobre CRON. Como usuario con privilegios de `root`, escriba el siguiente comando: `$ crontab -u <Magento file system owner name> -l`. Por ejemplo, en CentOS `$ crontab -u magento_user -l`. Si no se ha configurado ningún crontab para el usuario, se muestra el siguiente mensaje:    `no crontab for magento_user`. Su crontab le dice lo siguiente:
   * Qué binario de PHP está usando (en algunos casos, tiene más de uno)
   * Qué scripts cron de Adobe Commerce está ejecutando (en particular, las rutas a esos scripts)
   * Dónde se encuentran los registros de cron

   Consulte una de las siguientes secciones para ver una solución al problema.

## Solución: crontab no está configurado {#solution-crontab-not-set-up}

Para verificar que tus trabajos de cron estén configurados correctamente, consulta [Configurar trabajos de cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) en nuestra documentación para desarrolladores.

## Solución: cron ejecutándose desde un binario PHP incorrecto {#solution-cron-running-from-incorrect-php-binary}

Si su trabajo cron utiliza un binario de PHP diferente del plug-in del servidor web, los errores de configuración de PHP podrían mostrarse. Para resolver el problema, establezca una configuración PHP idéntica para la línea de comandos de PHP y el complemento del servidor web de PHP.

Para obtener más información sobre la configuración de PHP, consulte [Configuración de PHP requerida](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) en nuestra documentación para desarrolladores.

## Solución: cron se ejecuta con errores {#solution-cron-running-with-errors}

Intente ejecutar cada comando manualmente porque el comando puede mostrar mensajes de error útiles. Consulte [Configurar trabajos cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) en nuestra documentación para desarrolladores.

>[!NOTE]
>
>Debe ejecutar cron al menos *dos veces* para que se ejecute el trabajo; la primera vez que se pongan en cola los trabajos, la segunda vez que se ejecuten los trabajos.
