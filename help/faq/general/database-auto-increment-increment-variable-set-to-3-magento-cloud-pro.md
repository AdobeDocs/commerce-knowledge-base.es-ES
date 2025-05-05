---
title: La variable de incremento auto_increment de la base de datos está configurada en "3" Adobe Commerce en nuestra arquitectura Cloud Pro
description: Este es el comportamiento esperado para las soluciones de arquitectura de planificación de Adobe Commerce en la infraestructura en la nube Pro debido a la arquitectura de 3 nodos y no se puede modificar.
exl-id: ea478cbc-2dc2-41c9-8ea7-7e2f308e5948
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# La variable de incremento auto_increment de la base de datos está configurada en &quot;3&quot; Adobe Commerce en nuestra arquitectura Cloud Pro

Este es el comportamiento esperado para las soluciones de arquitectura de planificación de Adobe Commerce en la infraestructura en la nube Pro debido a la arquitectura de 3 nodos y no se puede modificar.

Se utiliza el clúster de base de datos Galera, que es un clúster de base de datos con una base de datos MariaDB MySQL por nodo con una configuración de incremento automático de tres para ID únicos en cada base de datos.

<u>¿Por qué el ID de incremento utilizado en los clústeres Pro no siempre se separa/incrementa en 3?</u>

El ID de incremento utilizado en los clústeres no siempre se separa/incrementa en 3 debido al modo en que funciona Galera.

Cada uno de los tres servidores gestiona su propio espacio de ID, y el incremento que se utiliza depende de cuál es el servidor de base de datos principal MySQL (según la carga relativa), por lo que los huecos varían.
Si se conecta SSH a cada nodo y se conecta a la instancia local de MySQL que se ejecuta en ese nodo usando el puerto 3307 (en lugar de estar proxy al &quot;principal&quot; en el puerto estándar 3306), verá la siguiente imagen:

![incremento_automático](assets/auto_increment_id.png)

Por ejemplo, si el nodo principal seleccionado es el nodo 1 donde `auto_increment_offset = 1`, el identificador se incrementaría en 1. A continuación, si se selecciona un nuevo nodo principal más adelante (por ejemplo, el nodo 3 donde `auto_increment_offset = 3`), se incrementará en 3.

## Vínculos útiles

Consulte en nuestra documentación para desarrolladores:

* [Nube para Adobe Commerce > Arquitectura Pro > Copia de seguridad y recuperación ante desastres](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [Nube para Adobe Commerce > Instalar requisitos previos: base de datos](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/overview)
