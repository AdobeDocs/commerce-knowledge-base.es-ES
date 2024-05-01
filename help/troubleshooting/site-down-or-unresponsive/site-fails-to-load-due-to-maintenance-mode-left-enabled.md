---
title: El sitio no se puede cargar debido a que el modo de mantenimiento se ha dejado habilitado
description: "Este artículo proporciona una corrección cuando el sitio no se carga debido a que el modo de mantenimiento se ha dejado habilitado o no se ha deshabilitado automáticamente. Puede recibir un mensaje de error: *Servicio temporalmente no disponible El servidor no puede atender temporalmente su solicitud debido a tiempo de inactividad de mantenimiento o problemas de capacidad.*"
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# El sitio no se puede cargar debido a que el modo de mantenimiento se ha dejado habilitado

Este artículo proporciona una corrección para los casos en los que el sitio no se carga debido a que el modo de mantenimiento se ha dejado habilitado o no se ha deshabilitado automáticamente. Puede recibir un mensaje de error: *Servicio Temporalmente no disponible El servidor no puede atender temporalmente su solicitud debido a un tiempo de inactividad de mantenimiento o problemas de capacidad.*

## Versiones y productos afectados

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x
* Adobe Commerce local 2.2.x, 2.3.x

## Problema

El modo de mantenimiento forma parte del proceso de implementación. Sin embargo, si se ha activado automáticamente y no se ha desactivado, o si el comerciante ha activado el modo de mantenimiento manualmente y ha olvidado desactivarlo, puede provocar un error en la implementación.

## Causa

Tener el modo de mantenimiento habilitado impide que el sitio se cargue.

## Solución

Para comprobar el estado actual del modo de mantenimiento, ejecute el siguiente comando desde la CLI:

```
bin/magento maintenance:status
```

Para desactivar el modo de mantenimiento, ejecute el siguiente comando en CLI:

```
bin/magento maintenance:disable
```

## Lectura relacionada

Para aprender a utilizar el modo de mantenimiento, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=maintenance%20mode) en nuestra documentación para desarrolladores.
