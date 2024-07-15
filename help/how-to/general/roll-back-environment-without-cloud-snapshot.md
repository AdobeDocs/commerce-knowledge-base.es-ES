---
title: Revertir entorno sin instantánea de nube
description: Este artículo muestra dos soluciones para revertir un entorno sin tener una instantánea de su entorno en Adobe Commerce en la infraestructura en la nube.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: 5347e8714ef1374440f5d246100a0221e4b189fc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Revertir entorno sin instantánea de nube

Este artículo muestra dos soluciones para revertir un entorno sin tener una instantánea de su entorno en Adobe Commerce en la infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Elija el más apropiado para su caso:

* Si tiene una compilación estable, pero no una instantánea válida - [Escenario 1: sin instantánea, compilación estable (conexión SSH disponible)](#scen2).
* Si la compilación está dañada y no tiene ninguna instantánea válida - [Escenario 2: Sin instantánea; compilación dañada (sin conexión SSH)](#scen3).

## Escenario 1: sin instantánea, compilación estable (conexión SSH disponible) {#scen2}

Esta sección muestra cómo revertir un entorno cuando no se ha creado una instantánea, pero se puede acceder al entorno a través de SSH.

Estos son los pasos:

1. Deshabilite la administración de configuración.
1. Desinstale el software de Adobe Commerce.
1. Restablezca la rama de Git.

Después de realizar estos pasos:

* su instalación de Adobe Commerce vuelve a su estado Vainilla (base de datos restaurada; configuración de implementación eliminada; directorios bajo `var` borrados)
* la rama de git se restablece al estado deseado en el pasado

Lea los pasos detallados a continuación:

### Paso 0 (requisito previo): Elimine config.php para deshabilitar la administración de la configuración {#disable_config_management}

Es necesario deshabilitar la administración de configuración para que no aplique automáticamente las opciones de configuración anteriores durante la implementación.

Para deshabilitar la administración de configuración, asegúrese de que el directorio `/app/etc/` no contenga los archivos `config.php` (para Adobe Commerce 2.4.x) o `config.local.php` (para Adobe Commerce 2.1.x).

Para quitar el archivo de configuración, siga estos pasos:

1. [SSH a su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Elimine el archivo de configuración:
   * Para Adobe Commerce 2.4:

   ```php
    rm app/etc/config.php
   ```

   * Para Adobe Commerce 2.1:

   ```php
     rm app/etc/config.local.php
   ```

Para obtener más información acerca de la administración de configuración, consulte:

* [Reduzca el tiempo de inactividad de la implementación en Adobe Commerce en la infraestructura en la nube](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) en nuestra base de conocimiento de asistencia.
* [Administración de configuración para la configuración de la tienda](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) en nuestra documentación para desarrolladores.

### Paso 1: Desinstalar el software de Adobe Commerce con el comando setup:uninstall {#setup-uninstall}


Al desinstalar el software de Adobe Commerce, se borra y restaura la base de datos, se quita la configuración de implementación y se borran los directorios de `var`.

Revise [Desinstalar el software de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) en nuestra documentación para desarrolladores.

Para desinstalar el software de Adobe Commerce, siga estos pasos:

1. [SSH a su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Ejecutar `setup:uninstall`:

   ```php
     php bin/magento setup:uninstall
   ```

1. Confirme la desinstalación.

El siguiente mensaje se muestra para confirmar que la desinstalación se ha realizado correctamente:

```php
[SUCCESS]: Magento uninstallation complete.
```

Esto significa que hemos revertido nuestra instalación de Adobe Commerce (incluida DB) a su estado auténtico (Vainilla).

### Paso 2: Restablecer la rama de Git {#reset-git-branch}

Con el restablecimiento de Git, revertimos el código al estado deseado en el pasado.

1. Clone el entorno en el entorno de desarrollo local. Puede copiar el comando en la consola de Cloud:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Acceda al historial de confirmaciones. Use `--reverse` para mostrar el historial en orden inverso para mayor comodidad:

   ```git
     git log --reverse
   ```

1. Seleccione el hash de compromiso en el que ha sido bueno. Para restablecer el código a su estado auténtico (Vainilla), busque la primera confirmación que creó su rama (entorno).    ![Seleccionar un hash de confirmación en la consola de Git](assets/select_commit_hash.png)
1. Aplicar restablecimiento de Git duro:

   ```git
     git reset --h <commit_hash>
   ```

1. Insertar cambios en el servidor:

   ```git
     git push --force <origin> <branch>
   ```

Después de realizar estos pasos, la rama de Git se restablece y todo el registro de cambios de Git es claro. La última inserción de Git déclencheur la reimplementación para aplicar todos los cambios y volver a instalar Adobe Commerce.

## Escenario 2: Sin instantánea, compilación dañada (sin conexión SSH) {#scen3}

En esta sección se muestra cómo revertir un entorno cuando está en un estado crítico: el procedimiento de implementación no puede generar una aplicación en funcionamiento, por lo que la conexión SSH no está disponible.

En este caso, primero debe restaurar el estado de trabajo de la aplicación de Adobe Commerce mediante el restablecimiento de Git y, a continuación, desinstalar el software de Adobe Commerce (para soltar y restaurar la base de datos, quitar la configuración de implementación, etc.). En este escenario se siguen los mismos pasos que en el escenario 1, pero el orden de los pasos es diferente y hay un paso adicional: forzar la reimplementación. Estos son los pasos:

[1. Restablezca la rama de Git.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Deshabilitar administración de configuración.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[3. Desinstale el software de Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&amp;period; Forzar reimplementación.

Después de realizar estos pasos, obtendrá los mismos resultados que en el escenario 1.

### Paso 4: Forzar el redespliegue

Realice una confirmación (puede ser una confirmación vacía, aunque no la recomendamos) y envíela al servidor para volver a implementarla en el déclencheur:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Si la instalación:desinstalación falla, restablecer la base de datos manualmente

Si al ejecutar el comando `setup:uninstall` se produce un error y no se puede completar, se puede borrar la base de datos manualmente siguiendo estos pasos:

1. [SSH a su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Conéctese a la base de datos MySQL:

   ```sql
   mysql -h database.internal
   ```

1. Soltar la base de datos `main`:

   ```sql
   drop database main;
   ```

1. Crear una base de datos `main` vacía:

   ```sql
   create database main;
   ```

1. Elimine los siguientes archivos de configuración: `config.php`, `config.php` `.bak`, `env.php` y `env.php.bak`.

Después de restablecer la base de datos, [inserte Git en el entorno para volver a implementar el déclencheur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) e instale Adobe Commerce en una base de datos recién creada. O [ejecute el comando de reimplementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [Restaurar una instantánea en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Crear una instantánea](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Administración de instantáneas y copias de seguridad](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Administrar ramas con Cloud Console: ver registros](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [Error de implementación de componente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [Administre su proyecto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
