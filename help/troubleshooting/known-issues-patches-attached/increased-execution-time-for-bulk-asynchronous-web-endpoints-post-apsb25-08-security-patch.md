---
title: Mayor tiempo de ejecución para extremos web asíncronos masivos después del parche de seguridad APSB25-08
description: Este artículo proporciona una revisión para el problema en el que las solicitudes POST rest/all/async/bulk/V1/products para más de 1000 entradas experimentan un tiempo de ejecución significativamente mayor después de aplicar el parche de seguridad APSB25-08.
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
exl-id: 784a48cb-1ef1-432b-b09f-ebcbb9bebf01
source-git-commit: f0c2e20e0bd6dab713be59c1c686ee2948445bd4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Mayor tiempo de ejecución para todos los extremos web asíncronos masivos posteriores al parche de seguridad APSB25-08

Este artículo proporciona una revisión para todos los extremos web asincrónicos masivos como `POST rest/all/async/bulk/V1/products` con más de 1000 entradas que experimentan tiempos de ejecución significativamente más largos después de aplicar el parche de seguridad APSB25-08.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12

* Adobe Commerce (todos los métodos de implementación) 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11

* Adobe Commerce (todos los métodos de implementación) 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p9

* Adobe Commerce (todos los métodos de implementación) 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4

* Adobe Commerce (todos los métodos de implementación) 2.4.8

## Problema

Después de aplicar el parche de seguridad APSB25-08, las solicitudes de `POST rest/all/async/bulk/V1/products` con más de 1000 entradas están tardando mucho más en ejecutarse.

<u>Pasos a seguir</u>:

1. Realice una solicitud `POST rest/all/async/bulk/V1/products` con más de 1000 entradas (el nombre, el SKU y la descripción son suficientes).
1. Tenga en cuenta el tiempo empleado para la solicitud.
1. Aplique el parche de seguridad APSB25-08 y limpie los datos y la caché generados mediante `se:di:co`.
1. Ejecutar `bin/magento c:f`.
1. Vaya a la tienda para asegurarse de que la caché y los archivos generados estén en su lugar.
1. Repita la solicitud desde el paso 1.
1. Tenga en cuenta el aumento de tiempo empleado para la solicitud.
1. Elimine el parche de seguridad APSB25-08, vacíe la caché, vuelva a generar el código y repita la solicitud del paso 1 para confirmar que el tiempo de ejecución vuelve a la normalidad. (Opcional)

<u>Resultados esperados</u>:

El tiempo de ejecución de `async/bulk` solicitudes ha aumentado significativamente después de aplicar el parche de seguridad.

<u>Resultados reales</u>:

El tiempo de ejecución de `async/bulk` solicitudes no debería haber aumentado significativamente después de aplicar el parche de seguridad, aunque se espera un cierto aumento en el tiempo.

## Solución

Para resolver el problema, aplique el [AC-14078-2-4x-composer-patch.zip](assets/AC-14078-2-4x-composer-patch.zip).

## Cómo aplicar el parche

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=es) en nuestra base de conocimiento de asistencia para obtener instrucciones.

## Lectura relacionada

* [Actualización de seguridad disponible para Adobe Commerce - APSB25-08](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-27149)
