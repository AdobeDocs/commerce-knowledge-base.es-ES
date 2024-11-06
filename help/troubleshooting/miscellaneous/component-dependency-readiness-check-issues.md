---
title: Problemas de comprobación de disponibilidad de dependencias del componente
description: Este artículo proporciona soluciones para los conflictos de dependencia de componentes.
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Problemas de comprobación de disponibilidad de dependencias del componente

Este artículo proporciona soluciones para los conflictos de dependencia de componentes.

## Resolver conflictos de dependencia de componentes {#resolve-component-dependency-conflicts}

Le sugerimos que pruebe las siguientes soluciones en el orden mostrado:

1. [Dependencias en conflicto](#trouble-depend-conflict)
1. [Problemas de permisos del sistema de archivos](#trouble-depend-permission)
1. [El estado de comprobación de dependencias del componente nunca cambia](#trouble-depend-state)

### Dependencias en conflicto {#trouble-depend-conflict}

El mensaje *Encontramos dependencias de componentes en conflicto* se muestra si Composer no puede determinar qué componentes instalar o actualizar. Para resolver los problemas de dependencia de componentes, debe ser un técnico que comprenda a fondo cómo funciona Composer.

A continuación se muestra un ejemplo de mensaje de error:

```bash
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>Es probable que el mensaje que vea sea diferente.

Consulte [Dependencias de componentes en conflicto para obtener una solución](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md) en nuestra base de conocimiento de soporte.

## Problemas de permisos del sistema de archivos {#trouble-depend-permission}

Si el propietario del sistema de archivos de Adobe Commerce no tiene permisos para escribir en directorios del sistema de archivos de Adobe Commerce, aparece un mensaje similar al siguiente:

```bash
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

Asegúrese de establecer permisos de sistema de archivos como se describe en el artículo [Información general sobre la propiedad y los permisos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) en nuestra documentación para desarrolladores.

## El estado de comprobación de dependencias del componente nunca cambia {#trouble-depend-state}

En algunos casos, el estado de la Comprobación de dependencias del componente no cambia, incluso después de intentar corregir los problemas. En ese caso, puede eliminar o cambiar el nombre de los archivos llamados `<magento_root>/var/.update_cronjob_status` y `<magento_root>/var/.setup_cronjob_status` e intentar ejecutar de nuevo el Administrador de componentes.

Al cambiar el nombre de estos archivos o eliminarlos, el Administrador de componentes debe volver a ejecutar las comprobaciones.
