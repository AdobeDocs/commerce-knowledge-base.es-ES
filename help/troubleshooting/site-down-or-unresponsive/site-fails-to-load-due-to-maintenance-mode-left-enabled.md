---
title: El sitio no se puede cargar debido a que el modo de mantenimiento se ha dejado habilitado
description: "Este artículo proporciona una corrección cuando el sitio no se carga debido a que el modo de mantenimiento se ha dejado habilitado o no se ha deshabilitado automáticamente. Puede recibir un mensaje de error: *Servicio temporalmente no disponible El servidor no puede atender temporalmente su solicitud debido a tiempo de inactividad de mantenimiento o problemas de capacidad.*"
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# El sitio no se puede cargar debido a que el modo de mantenimiento se ha dejado habilitado

Este artículo proporciona una corrección para los casos en los que el sitio no se carga debido a que el modo de mantenimiento se ha dejado habilitado o no se ha deshabilitado automáticamente. Es posible que reciba un mensaje de error: *Servicio temporalmente no disponible El servidor no puede atender temporalmente su solicitud debido a tiempo de inactividad de mantenimiento o problemas de capacidad.*

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

Para saber cuándo usar el modo de mantenimiento, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en nuestra documentación para desarrolladores.
