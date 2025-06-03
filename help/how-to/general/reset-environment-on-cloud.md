---
title: Restablecer el entorno en Adobe Commerce en la infraestructura en la nube
description: Este artículo muestra diferentes escenarios de reversión de un entorno en Adobe Commerce en una infraestructura en la nube.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: 4327f464fb8eebf30a380e9e58afe55c3e613e52
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# Restablecer el entorno en Adobe Commerce en la infraestructura en la nube

Este artículo muestra diferentes escenarios de reversión de un entorno en Adobe Commerce en una infraestructura en la nube.
>[!NOTE]
>
>Esta guía se aplica a todos los entornos de Cloud Starter y solo a los entornos de integración en Cloud Pro.

Elija el más apropiado para su caso:

* Si tiene una actividad planificada (implementación o actualización planificada) - [Escenario 1: actividad planificada)](#scen1).
* Si tiene una instantánea válida: [Escenario 2: restaurar una instantánea](#scen2).
* Si tiene una compilación estable, pero no una instantánea válida - [Escenario 3: sin instantánea, compilación estable (conexión SSH disponible)](#scen3).
* Si la compilación está dañada y no tiene ninguna instantánea válida: [Escenario 4: sin instantánea; compilación dañada (sin conexión SSH)](#scen4).

## Escenario 1: actividad planificada

Con una implementación o actualización planificada, el [!UICONTROL Rollback] más fácil y recomendado sería que el comerciante, como parte de sus preparativos, hiciera lo siguiente:

>[!NOTE]
>
>Pruebe siempre primero estos pasos en su entorno inferior.

<u>Cinco días antes de las actividades de actualización/implementación</u>:

1. Comprobar el tamaño de la base de datos actual.
1. Compruebe que tiene suficiente espacio en disco en `/data/exports` para guardar un [!UICONTROL Database Dump]. Si no tiene suficiente espacio en disco, elimine los datos no deseados o cree un caso de asistencia y solicite que se expanda el disco.

<u>El día de los cambios</u>:

1. Coloque el sitio web en [!UICONTROL Maintenance Mode].
Obtenga más información sobre [Habilitar o deshabilitar [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html?lang=es) en nuestra guía del usuario y [[!UICONTROL Maintenance Mode] opciones para la actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html?lang=es) en nuestra guía de actualización.
1. Deshabilitar trabajos cron. Obtenga más información sobre cómo deshabilitar los trabajos de cron en nuestra [guía de propiedades de cron](<https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property#disable-cron-jobs>).
1. Tome un(a) [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html?lang=es) local.

<u>Si se requiere [!UICONTROL Rollback]</u>:

1. Si aplicaciones como [!DNL MariaDB] se actualizaron como parte de esta actividad planificada, primero debe reinstalar la aplicación a una versión anterior.
1. [!UICONTROL Rollback] la base de datos con el [!UICONTROL Database Dump] local y vuelva a importarla en [!DNL MariaDB].
1. [!UICONTROL Rollback] cambió el código a través de [!DNL Git] a una versión de trabajo anterior.

No se recomienda usar [!UICONTROL Snapshots] para la actividad [!UICONTROL rollbacks/restores] de actualización o planeada, ya que se tarda mucho más en recuperar los datos en comparación con un [!UICONTROL Database Dump] local, como se ha indicado anteriormente en el paso 2 de la sección **Si se requiere un [!UICONTROL Rollback]**.

[!UICONTROL Snapshots] no se mantienen en el nodo o servidor, se mantienen en un bloque de almacenamiento independiente y, como esos datos deben transmitirse desde el almacenamiento del bloque a través de la red a un nuevo disco, lleva tiempo en el proceso. A continuación, ese nuevo disco se monta en el nodo listo para recuperarlo o importarlo en el disco original conectado al nodo o servidor.

Cuando compara esto con la importación de un(a) [!UICONTROL Database Dump] local(a), los datos ya se pueden recuperar en el nodo/servidor, por lo que se guarda mucho tiempo, ya que solo se requiere un(a) [!UICONTROL Database Import].

## Escenario 2: restaurar una instantánea

Lea: [Restaure una instantánea de Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-snapshot) en nuestra documentación para desarrolladores.

>[!NOTE]
>
>La creación de una instantánea debe ser nuestro primer paso después de acceder a Adobe Commerce en la cuenta de infraestructura de la nube y antes de aplicar cambios importantes. Es una práctica recomendada y muy recomendable.

Lectura: [Crear una instantánea](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-snapshot) en nuestra documentación para desarrolladores.

## Escenario 3: sin instantánea, compilación estable (conexión SSH disponible)

Esta sección muestra cómo restablecer un entorno cuando no se ha creado una instantánea, pero se puede acceder al entorno a través de SSH.

Estos son los pasos:

1. Deshabilite la administración de configuración.
1. Desinstale el software de Adobe Commerce.
1. Restablezca la rama [!DNL git].

Después de realizar estos pasos:

* Su instalación de Adobe Commerce vuelve a su estado Vainilla (base de datos restaurada; configuración de implementación eliminada; directorios bajo `var` borrados).
* La rama [!DNL git] se restableció al estado deseado en el pasado.

Lea los pasos detallados a continuación.

### Paso 0 (requisito previo): Elimine config.php para deshabilitar la administración de la configuración

Es necesario deshabilitar la administración de configuración para que no aplique automáticamente las opciones de configuración anteriores durante la implementación.

Para deshabilitar la administración de configuración, asegúrese de que el directorio `/app/etc/` no contenga el archivo `config.php`.

Para quitar el archivo de configuración, siga estos pasos:

1. [SSH a su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=es).
1. Quitar el archivo de configuración: `rm app/etc/config.php`

Más información sobre la Administración de configuración:

* [Reduzca el tiempo de inactividad de la implementación en Adobe Commerce en la infraestructura en la nube](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) en nuestra base de conocimiento de asistencia.
* [Administración de configuración para la configuración de la tienda](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=es) en nuestra documentación para desarrolladores.

### Paso 1: Desinstalar el software de Adobe Commerce con el comando setup:uninstall


Al desinstalar el software de Adobe Commerce, se borra y restaura la base de datos, se quita la configuración de implementación y se borran los directorios de `var`.

Lea: [Desinstale el software de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html?lang=es) en nuestra documentación para desarrolladores.

Para desinstalar el software de Adobe Commerce, siga estos pasos:

1. [SSH a su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=es).
1. Ejecutar `setup:uninstall` : `bin/magento setup:uninstall`
1. Confirme la desinstalación.

El siguiente mensaje se muestra para confirmar que la desinstalación se ha realizado correctamente:

```php
[SUCCESS]: Magento uninstallation complete.
```

Esto significa que hemos revertido nuestra instalación de Adobe Commerce (incluida DB) a su estado auténtico (Vainilla).

### Paso 2: Restablecer la rama [!DNL git]

Con [!DNL git] restablecido, revertimos el código al estado deseado en el pasado.

1. Clone el entorno en el entorno de desarrollo local. Puede copiar el comando en la consola de Cloud:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Acceda al historial de confirmaciones. Use `--reverse` para mostrar el historial en orden inverso para mayor comodidad: `git log --reverse`
1. Seleccione el hash de compromiso en el que ha sido bueno. Para restablecer el código a su estado auténtico (Vainilla), busque la primera confirmación que creó su rama (entorno).
   ![texto alternativo](image.png)
1. Aplicar restablecimiento [!DNL git] duro: `git reset --h <commit_hash>`
1. Insertar cambios en el servidor: `git push --force <origin> <branch>`

Después de realizar estos pasos, la rama [!DNL git] se restablece y el registro de cambios [!DNL git] completo está borrado. La última [!DNL git] déclencheur la reimplementación para aplicar todos los cambios y volver a instalar Adobe Commerce.

## Escenario 4: sin instantánea; compilación dañada (sin conexión de [!DNL SSH])

Esta sección muestra cómo restablecer un entorno cuando se encuentra en un estado crítico: el procedimiento de implementación no puede generar correctamente una aplicación de trabajo, por lo que la conexión [!DNL SSH] no está disponible.

En este escenario, primero debe restaurar el estado de trabajo de la aplicación de Adobe Commerce mediante [!DNL git] reset, luego desinstale el software de Adobe Commerce (para soltar y restaurar la base de datos, quitar la configuración de implementación, etc.). En este escenario se siguen los mismos pasos que en el escenario 3, pero el orden de los pasos es diferente y hay un paso adicional: forzar la reimplementación. Estos son los pasos:

1. [Restablezca la rama  [!DNL git] .](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [Deshabilite la administración de configuración.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [Desinstale el software de Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. Forzar redespliegue.

Después de realizar estos pasos, obtendrá los mismos resultados que en el escenario 3.

### Paso 4: Forzar el redespliegue

Realice una confirmación (puede ser una confirmación vacía, aunque no la recomendamos) y envíela al servidor para volver a implementarla en el déclencheur:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Si la instalación:desinstalación falla, restablecer la base de datos manualmente

Si al ejecutar el comando `setup:uninstall` se produce un error y no se puede completar, se puede borrar la base de datos manualmente siguiendo estos pasos:

1. [SSH a su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=es).
1. Conéctese a MySQL DB: `mysql -h database.internal` (para entornos Pro, consulte: [Configurar el servicio MySQL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html?lang=es)).
1. Soltar la base de datos `main`: `drop database main;`
1. Crear una base de datos `main` vacía: `create database main;`
1. Eliminar los siguientes archivos de configuración: `config.php`, `config.php.bak`, `env.php`, `env.php.bak`

Después de restablecer la base de datos, [inserte [!DNL git] el entorno para volver a implementar el déclencheur](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html?lang=es) e instale Adobe Commerce en una base de datos recién creada. O [ejecute el comando de reimplementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=es#environment-commands).
