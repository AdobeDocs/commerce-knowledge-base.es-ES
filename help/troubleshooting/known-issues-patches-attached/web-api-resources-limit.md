---
title: La API web no puede procesar solicitudes con más de 20 elementos en la matriz
description: Este artículo proporciona una solución para el problema en el que la API web no puede procesar un mensaje que contenga más de 20 elementos en la matriz para Adobe Commerce 2.4.3.
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# La API web no puede procesar solicitudes con más de 20 elementos en la matriz

Este artículo proporciona una solución para el problema en el que la API web no puede procesar un mensaje que contenga más de 20 elementos en la matriz para Adobe Commerce 2.4.3.

## Productos y versiones afectados:

* Adobe Commerce (todos los métodos de implementación) 2.4.3 y 2.3.7-p1
* Magento Open Source 2.4.3 y 2.3.7-p1

## Problema

La API web no puede procesar el mensaje (por ejemplo, Actualización de stock) que contiene más de 20 elementos en la matriz.

## Causa

En Adobe Commerce 2.4.3, la limitación de velocidad integrada se añadió a las API de Magento para evitar ataques de denegación de servicio (DoS).

De forma predeterminada, está disponible la siguiente limitación de velocidad de API integrada:

* Las solicitudes REST que contienen entradas que representan una lista de entidades se limitan a un máximo predeterminado de 20 entidades
* Las consultas REST y GraphQL que permiten resultados paginados están limitadas a un máximo predeterminado de 300 elementos por página

## Solución

Para deshabilitar los límites de entrada en la solicitud de API de REST, aplique uno de los siguientes parches (según su versión):

* [MC-43048__set_rate_limits__2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048__set_rate_limits__2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### Versiones de Adobe Commerce compatibles

Los parches se han creado para:

* Adobe Commerce en la infraestructura en la nube 2.4.3 y 2.3.7-p1
* Adobe Commerce local 2.4.3 y 2.3.7-p1

Los parches no son compatibles con ninguna otra versión de Adobe Commerce.

### Cómo aplicar el parche

Descomprima el archivo descargado `.zip` y aplique el parche como se describe en [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

>[!WARNING]
>
>Si sospecha que su tienda está experimentando un ataque de denegación de servicio, Adobe recomienda reducir los límites de entrada predeterminados a un valor más bajo para imponer restricciones en el número de recursos que se pueden solicitar.  Puede personalizar los límites predeterminados mediante programación [argumentos del constructor de clase](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html)
>como se describe en nuestra documentación para desarrolladores: [Seguridad de API > Limitación de velocidad > Entradas máximas de parámetros](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting).

## Lectura relacionada

[Seguridad de API > Limitación de velocidad](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting) en nuestra documentación para desarrolladores.
