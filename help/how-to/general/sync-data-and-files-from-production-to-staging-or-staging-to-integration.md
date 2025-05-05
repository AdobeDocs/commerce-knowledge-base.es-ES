---
title: Sincronizar datos y archivos de producción con ensayo o ensayo con integración
description: En este artículo se explica cómo sincronizar el entorno de producción con el ensayo en Adobe Commerce en la infraestructura en la nube; esto no es posible.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Sincronizar datos y archivos de producción con ensayo o ensayo con integración

En este artículo se explica cómo sincronizar el entorno de producción con el entorno de ensayo en Adobe Commerce en la infraestructura en la nube; esto no es posible mediante la interfaz de usuario o la CLI de nube de Magento.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.3.x, 2.4.x

## Para sincronizar datos de un entorno a otro

Para sincronizar los datos, debe volcar manualmente la base de datos desde el entorno de origen. Para transferir datos a otro entorno, debe cargar el volcado de origen en el entorno de destino e importarlo. Para obtener más información, consulte [Importar código Adobe Commerce en un proyecto de Cloud > Importar base de datos de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) en nuestra documentación para desarrolladores.

Para la arquitectura de plan Pro de Adobe Commerce en la infraestructura en la nube, también puede sincronizar desde Ensayo y producción a su rama maestra de integración. Esta sincronización solo extrae y inserta código, no datos. Para sincronizar datos, deberá volcar los datos de la base de datos y enviarlos a la base de datos de otro entorno.

>[!WARNING]
>
>La sincronización de la base de datos no se puede realizar en los clústeres de ensayo y producción de Pro.

## Para sincronizar archivos de un entorno a otro

Para sincronizar archivos de un entorno a otro, use el comando `rsync`. Para obtener más información, consulte [Implementar código y migrar datos y archivos estáticos > Migrar archivos mediante rsync](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production#migrate-files-using-rsync) en nuestra documentación para desarrolladores.

>[!NOTE]
>
>Si desea sincronizar el código de integración a ensayo, debe hacerlo desde la rama de integración. Para ver los pasos, consulte [Sincronización del elemento principal del entorno](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment) en nuestra documentación para desarrolladores.
