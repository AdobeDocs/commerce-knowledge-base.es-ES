---
title: Los cambios en las categorías no se guardan
description: Este artículo proporciona una corrección para cuando se actualizan categorías de productos a través del administrador de Commerce, los cambios no se muestran en el administrador y la tienda. El problema se debe a los datos dañados en la tabla "catalog_category_entity". Para resolver el problema, corrija o elimine los registros de actualización de categoría problemáticos de la tabla. Después, debe poder actualizar las categorías de productos mediante el administrador.
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# Los cambios en las categorías no se guardan

Este artículo proporciona una corrección para cuando se actualizan categorías de productos a través del administrador de Commerce, los cambios no se muestran en el administrador y la tienda. El problema se debe a los datos dañados de la tabla `catalog_category_entity`. Para resolver el problema, corrija o elimine los registros de actualización de categoría problemáticos de la tabla. Después, debe poder actualizar las categorías de productos mediante el administrador.

## Problema

Después de realizar cambios en una categoría de producto en Administración y guardar, las nuevas actualizaciones no se guardan ni se muestran en Administración y tienda.

### Pasos a seguir

1. Vaya a **Catálogo** > **Categorías**.
1. Seleccione una categoría.
1. Realice cambios y haga clic en **Guardar**.
1. Se muestra el mensaje: *Ha guardado la categoría*.
1. Observe que el cambio que ha realizado no se ha guardado.

## Posible causa: datos dañados en la tabla `catalog_category_entity`

El problema se debe a los mismos valores de la columna `created_in` de los registros de categoría afectados de la base de datos (DB).

![Datos dañados en la tabla catalog_category_entity](assets/catalog_category_entity.png)

Detalles:

* La tabla de la base de datos `catalog_category_entity` tiene dos o más registros para la categoría afectada (estos registros tienen el mismo valor `entity_id`).
* Estos registros de categoría tienen **los mismos valores en la columna `created_in`**.

### ¿Cómo aparece la segunda entrada de la base de datos (y todas las siguientes) en la base de datos para una misma categoría?

El segundo registro de la base de datos (y, posiblemente, los siguientes) para la categoría afectada significa que ha habido actualizaciones de categoría programadas mediante el módulo Magento\_Ensayo. El módulo crea un registro adicional para una categoría en `catalog_category_entity` y ese es el comportamiento esperado de la aplicación; el problema es que los registros tienen los mismos valores para la columna `created_in`.

### ¿Cómo aparecen los mismos valores?

No podemos exponer con certeza las razones de la corrupción de datos. Las posibles razones pueden incluir:

* personalizaciones (código, temáticas, etc.)
* migración de datos incorrecta
* restauración de datos incorrecta desde la copia de seguridad

Hasta donde sabemos, estos datos dañados no son típicos de las instancias de Adobe Commerce &quot;limpias&quot; (listas para usar) y no se pueden reproducir en una instalación de Adobe Commerce sin personalizaciones.

### Comprobar si este es su problema

La tabla `catalog_category_entity` debe tener varios registros para la categoría afectada (los registros deben tener el mismo valor `entity_id`) y al menos dos de esos registros deben tener los mismos valores `created_in`. Con esto, las actualizaciones programadas de ensayo no se mostrarían en el administrador de Commerce; solo vería el bloque vacío Cambios programados.

#### Pasos a verificar

1. Acceda a la tabla catalog\_category\_entity de la base de datos.
1. Filtre las entidades por entity\_id, con entity\_id identificando la categoría afectada.
1. Si los valores de la columna created\_in son los mismos para diferentes entradas con la misma entidad\_id, ese es nuestro caso. Normalmente, los valores de `created_in` son diferentes para cada registro.

![Datos dañados en la tabla catalog_category_entity](assets/catalog_category_entity.png)

## Solución

Puede elegir una de las siguientes soluciones:

1. **Eliminar** los registros de actualización de categoría problemática
1. **Reparar** los registros de actualización de categoría problemática

### Eliminar los registros de actualización de categoría problemáticos

En esta solución, deberá establecer el valor `updated_in` correcto para el registro de categoría inicial y eliminar todos los demás registros para esta categoría. Esto elimina todas las actualizaciones de categoría programadas.

Siga estos pasos:

1. Busque los registros de la base de datos con `entity_id` de la categoría afectada.
1. Seleccione el registro con el mayor entero de la columna `updated_in`.
1. Copie el valor `updated_in` del registro seleccionado.
1. Seleccione el registro con `row_id` = `entity_id` (registro de categoría inicial) y pegue el valor copiado en la columna `updated_in` de este registro.
1. Eliminar fila(s) con `row_id` no igual a `entity_id`

### Repare los registros de actualización de categoría problemáticos

1. Busque los registros de categoría con el mismo `entity_id` y el mismo valor `created_in`.
1. Seleccione el registro donde `row_id` = `entity_id` y copie el valor `updated_in`.
1. Seleccione el registro donde `row_id` no es igual a `entity_id` y pegue el valor `updated_in` copiado como el valor `created_in`. Consulte la captura de pantalla siguiente como ilustración.    ![Copiando el valor created_in.png](assets/copy_created-in_value.png)
1. Compruebe que el registro de actualización de categoría, cuyo valor `created_in` ha actualizado (en el paso 3), existe en la tabla `staging_update`. *Por ejemplo:* SI el valor `created_in` copiado es 1509281953, ENTONCES la entidad con `row_id` = 1509281953 debe existir en la tabla `staging_update`.

## Lectura relacionada

[Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
