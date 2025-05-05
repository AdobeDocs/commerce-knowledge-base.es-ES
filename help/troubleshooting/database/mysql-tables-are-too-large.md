---
title: '[!DNL MySQL] tablas son demasiado grandes'
description: Este artículo explica por qué es un problema cuando una  [!DNL MySQL] tabla supera los 1 GB y cómo evitarlo.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL] tablas son demasiado grandes

Este artículo explica por qué es un problema cuando cualquier tabla de [!DNL MySQL] supera los 1 GB y cómo evitarlo.

## Productos y versiones afectados:

* Adobe Commerce en infraestructura en la nube 2.x.x
* Adobe Commerce local 2.x.x

## Problema

El tamaño de las tablas [!DNL MySQL] no afecta directamente al rendimiento del sitio. Sin embargo, si una tabla es grande, significa que hay operaciones de inserción frecuentes en esta tabla, con posibles datos adicionales o datos obsoletos. [!DNL MySQL] está diseñado para bases de datos, donde la relación entre operaciones de lectura y escritura es del 80%/20%.  Para las tablas grandes, de 1 GB o más, los índices [!DNL MySQL], diseñados para acelerar el rendimiento en las operaciones de lectura, podrían reducir el rendimiento en las operaciones de escritura.

## Solución

Tenga en cuenta las siguientes opciones para evitar una disminución del rendimiento:

* Cree un trabajo CRON que limpie las tablas grandes. Consulte [Buscar tablas grandes [!DNL MySQL] 2&rbrace; en nuestra base de conocimientos de soporte técnico para obtener recomendaciones sobre cómo identificar tablas grandes.](/help/how-to/general/find-large-mysql-tables.md)
* Para tablas de más de 1 GB, utilice un motor [!DNL MySQL] optimizado para la escritura de registros. Por ejemplo, el motor de archivado.
* Actualice la funcionalidad para evitar almacenar registros en la base de datos.

## Lectura relacionada

* [Tablas de registro de cambios sobredimensionadas que causan retrasos en las actualizaciones de entidades](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront) en nuestra base de conocimiento de soporte
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
