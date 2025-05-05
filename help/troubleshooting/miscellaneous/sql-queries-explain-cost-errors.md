---
title: "Consultas SQL: EXPLICAR errores de coste"
description: Este artículo proporciona soluciones para los errores de coste EXPLAIN cuando se ejecutan consultas SQL fallidas. PostgreSQL utiliza algo llamado [el comando EXPLAIN](https://www.postgresql.org/docs/9.5/static/using-explain.html) para determinar el coste de las consultas SQL. Creamos el Report Builder SQL para que también utilice este comando, lo que significa que si el coste se considera demasiado alto (la cantidad de recursos necesarios para ejecutar la consulta supera nuestros umbrales), la consulta no se ejecutará y se mostrará el mensaje EXPLAIN.
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Consultas SQL: EXPLICAR errores de coste

Este artículo proporciona soluciones para los errores de coste EXPLAIN cuando se ejecutan consultas SQL fallidas. PostgreSQL usa algo llamado [el comando EXPLAIN](https://www.postgresql.org/docs/9.5/static/using-explain.html) para determinar el costo de las consultas SQL. Creamos el Report Builder SQL para que también utilice este comando, lo que significa que si el coste se considera demasiado alto (la cantidad de recursos necesarios para ejecutar la consulta supera nuestros umbrales), la consulta no se ejecutará y se mostrará el mensaje EXPLAIN.

Esto puede deberse a varias razones. A continuación se indican los mensajes que podría recibir, qué significan y cómo solucionarlos.

## No se puede ejecutar la consulta. El valor de costo EXPLAIN de \[xxx\] es demasiado alto para ejecutar esta consulta.

Si ve este mensaje, significa que la consulta se consideró demasiado costosa para ejecutarse. Tenemos dos recomendaciones para esta situación: una es eliminar cualquier cláusula ORDER BY de la consulta, ya que son operaciones costosas. El segundo es seguir las sugerencias de nuestro [artículo de optimización](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html?lang=es) para modificar su consulta.

## No se puede ejecutar la consulta. Esta consulta devuelve \[xxx\] filas, lo que supera el límite de 10 000

En este caso, el número posible de resultados excede el máximo establecido para el Report Builder SQL. Hay varias formas de reducir la cantidad de resultados:

* Intente agregar algunos filtros a la consulta.
* Utilice LIMIT, si puede. Algunas tablas tienen un gran número de filas y limitar los resultados puede mantenerle por debajo del límite de filas.

## No se puede analizar la respuesta EXPLAIN.

¡Uy! Este mensaje normalmente significa que algo probablemente salió mal en nuestro extremo. Si sigue recibiendo este error, póngase en contacto con el servicio de asistencia.
