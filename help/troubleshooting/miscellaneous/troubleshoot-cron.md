---
title: Solucionar problemas de cron
description: Este artículo ofrece soluciones de solución de problemas para problemas con cron en productos locales de Adobe Commerce.
exl-id: e69a4fb3-731b-449e-a815-c33cd2faa567
feature: Configuration
role: Developer
source-git-commit: b6a79bcff3d757d40e7070182d8853a37960a782
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Solucionar problemas de cron

Este artículo ofrece soluciones de solución de problemas para problemas con cron en productos locales de Adobe Commerce.

## Productos y versiones afectados

* Adobe Commerce local 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problemas

## Los siguientes son síntomas de problemas crónicos:

* La actualización o actualización nunca se ejecuta; permanece en un `pending` estado.
* Un mensaje de error acerca de [PHP](https://glossary.magento.com/php) configuración `$HTTP_RAW_POST_DATA` se muestra aunque esté configurado correctamente.
* La comprobación de disponibilidad de CRON falla. Los posibles errores incluyen rutas no grabables y cron no configurado. A continuación se muestra un ejemplo:

  ![upgr-tshoot-no-cron2.png](assets/upgr-tshoot-no-cron2.png)

* La comprobación de disponibilidad de PHP no muestra la versión de PHP como se muestra en la siguiente figura.

  ![Screen_Shot_2019-08-29_at_1.36.08_PM.png](assets/Screen_Shot_2019-08-29_at_1.36.08_PM.png)

* Se muestra el siguiente error en el Administrador de Commerce:

  ![comando-cron-not-running.png](assets/compman-cron-not-running.png)

Para ver el error, es posible que tenga que hacer clic en **Mensajes del sistema** en la parte superior de la ventana, como se indica a continuación:

![compman_sys-messages.png](assets/compman_sys-messages.png)

## Investigue para encontrar la causa {#check-your-existing-crontab}

En esta sección se explica cómo ver si cron se está ejecutando actualmente y comprobar si está configurado correctamente.

Para verificar si su crontab está configurado, haga los siguientes pasos:

1. Inicie sesión en el servidor de Magento como o cambie a [propietario del sistema de archivos de Magento](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html).
1. Compruebe si existe el siguiente archivo:    `bash    ls -al <magento_root>/var/.setup_cronjob_status`. Si el archivo existe, cron se ha ejecutado correctamente en el pasado. Si el archivo *no tiene* existe, o bien aún no ha instalado Magento o cron no se está ejecutando. En cualquier caso, continúe con el siguiente paso.
1. Obtenga más información sobre CRON. Como usuario con `root` privilegios, introduzca el siguiente comando:    `bash    crontab -u <Magento file system owner name> -l`. Por ejemplo, en CentOS `bash    crontab -u magento_user -l`.  Si no se ha configurado ningún crontab para el usuario, se muestra el siguiente mensaje:    `terminal    no crontab for magento_user`. Su crontab le dice lo siguiente:

   * Qué binario de PHP está usando (en algunos casos, tiene más de uno)
   * Qué scripts cron de Magento está ejecutando (en particular, las rutas a esos scripts)
   * Dónde se encuentran los registros de cron

Consulte una de las siguientes secciones para ver una solución al problema.

## Soluciones

### No se ha configurado la solución para crontab {#solution-crontab-not-set-up}

Para comprobar que los trabajos de cron están correctamente configurados, consulte [Configuración de trabajos cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

### Solución para cron que se ejecuta desde un binario PHP incorrecto {#solution-cron-running-from-incorrect-php-binary}

Si su trabajo cron utiliza un binario de PHP diferente del plug-in del servidor web, los errores de configuración de PHP podrían mostrarse. Para resolver el problema, establezca una configuración PHP idéntica para la línea de comandos de PHP y el complemento del servidor web de PHP.

Para obtener más información sobre la configuración de PHP, consulte [Configuración de PHP requerida](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) en nuestra documentación para desarrolladores.

### Solución para cron que se ejecuta con errores {#solution-cron-running-with-errors}

Intente ejecutar cada comando manualmente porque el comando puede mostrar mensajes de error útiles. Consulte [Configuración de trabajos cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

>[!NOTE]
>
>Debe ejecutar cron al menos *dos veces* para que se ejecute el trabajo; la primera vez que se ponen en cola los trabajos, la segunda vez que se ejecutan los trabajos.
