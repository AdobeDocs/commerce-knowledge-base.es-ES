---
title: Las tablas MySQL son demasiado grandes
description: Este artículo explica por qué es un problema cuando cualquier tabla MySQL supera los 1 GB y cómo evitarlo.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Las tablas MySQL son demasiado grandes

Este artículo explica por qué es un problema cuando cualquier tabla MySQL supera los 1 GB y cómo evitarlo.

## Productos y versiones afectados:

* Adobe Commerce en infraestructura en la nube 2.x.x
* Adobe Commerce local 2.x.x

## Problema

El tamaño de las tablas MySQL no afecta directamente al rendimiento del sitio. Sin embargo, si una tabla es grande, significa que hay operaciones de inserción frecuentes en esta tabla, con posibles datos adicionales o datos obsoletos. MySQL está diseñado para bases de datos, donde la proporción entre operaciones de lectura/escritura es del 80%/20%.  Para las tablas grandes, de 1 GB y más, los índices MySQL, que están diseñados para acelerar el rendimiento en las operaciones de lectura, podrían degradar el rendimiento en las operaciones de escritura.

## Solución

Tenga en cuenta las siguientes opciones para evitar una disminución del rendimiento:

* Cree un trabajo CRON que limpie las tablas grandes. Consulte [Buscar tablas MySQL grandes](/help/how-to/general/find-large-mysql-tables.md) en nuestra base de conocimiento de soporte para obtener recomendaciones sobre cómo identificar tablas grandes.
* Para tablas de más de 1 GB, utilice un motor MySQL optimizado para la escritura de registros. Por ejemplo, el motor de archivado.
* Actualice la funcionalidad para evitar almacenar registros en la base de datos.

## Lectura relacionada

[Tablas de registro de cambios sobredimensionadas que causan retrasos en las actualizaciones de entidades](/help/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront.md) en nuestra base de conocimiento de soporte.
