---
title: Error al purgar la caché en el administrador de Commerce
description: 'Este artículo explica cómo identificar la causa de un mensaje de error que se produce al purgar la caché en el administrador de Commerce. Cuando intente purgar la caché a través del administrador, recibirá el siguiente mensaje:'
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Error al purgar la caché en el administrador de Commerce

En este artículo se explica cómo identificar la causa de un mensaje de error que se produce al purgar la caché en el administrador de Commerce. Cuando intente purgar la caché a través del administrador, recibirá el siguiente mensaje:
El archivo */app/project-id/pub/media/catalog/product/cache/directory/filename&quot; no se puede eliminar. Advertencia:!unlink(/app/project id/pub/media/catalog/product/cache/directory/filename): no existe ese archivo o directorio*

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.3.0-2.3.7, 2.4.0-2.4.2-p1

## Problema

Cuando intente purgar la caché a través del administrador, recibirá un mensaje de error.

<u>Pasos a seguir:</u>

1. En el Administrador, vaya a **Sistema** > **Herramientas** > **Administración de caché**.
1. Seleccione cualquiera de las opciones para borrar el almacenamiento en caché.

<u>Resultado esperado:</u>

Se ha vaciado correctamente la caché de Adobe Commerce sin errores.

<u>Resultado real:</u>

Recibe el error &quot;el archivo no se puede eliminar&quot;.

## Causa

El error está relacionado con un retraso entre el momento en que se inició la operación de limpieza de la caché y el momento en que se informó como completada.

## Solución

1. Confirme que los archivos mencionados en el error no están presentes en el servidor (comprobando que la depuración de la caché se haya realizado correctamente):

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

Si ve el siguiente resultado:

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

se intentó borrar los archivos cuando ya se había completado la operación. Esto no es un error; es un problema de concurrencia de mensajería que se espera que ocurra a veces. No hay problema para solucionar.
Sin embargo, si el resultado muestra que los archivos aún están en la caché, debe [enviar un vale de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lectura relacionada

* [Administración de caché](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) en nuestra documentación para desarrolladores.
