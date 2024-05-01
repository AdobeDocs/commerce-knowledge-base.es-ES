---
title: Los cambios en las categorías no se guardan
description: Este artículo proporciona una corrección para cuando se actualizan categorías de productos a través del administrador de Commerce, los cambios no se muestran en el administrador y la tienda. El problema se debe a los datos dañados en la tabla "catalog_category_entity". Para resolver el problema, corrija o elimine los registros de actualización de categoría problemáticos de la tabla. Después, debe poder actualizar las categorías de productos mediante el administrador.
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# Los cambios en las categorías no se guardan

Este artículo proporciona una corrección para cuando se actualizan categorías de productos a través del administrador de Commerce, los cambios no se muestran en el administrador y la tienda. El problema se debe a los datos dañados en la `catalog_category_entity` tabla. Para resolver el problema, corrija o elimine los registros de actualización de categoría problemáticos de la tabla. Después, debe poder actualizar las categorías de productos mediante el administrador.

## Problema

Después de realizar cambios en una categoría de producto en Administración y guardar, las nuevas actualizaciones no se guardan ni se muestran en Administración y tienda.

### Pasos a seguir

1. Ir a **Catálogo** > **Categorías**.
1. Seleccione una categoría.
1. Realice cambios y haga clic en **Guardar**.
1. Se muestra el siguiente mensaje: *Ha guardado la categoría*.
1. Observe que el cambio que ha realizado no se ha guardado.

## Posible causa: datos dañados en el `catalog_category_entity` tabla

El problema se debe a los mismos valores en la variable `created_in` de los registros de categoría afectados en la base de datos (BD).

![Datos dañados en la tabla catalog_category_entity](assets/catalog_category_entity.png)

Detalles:

* El `catalog_category_entity` La tabla de base de datos tiene dos o más registros para la categoría afectada (estos registros tienen el mismo valor `entity_id` valor).
* Estos registros de categoría tienen **los mismos valores en la variable `created_in` columna**.

### ¿Cómo aparece la segunda entrada de la base de datos (y todas las siguientes) en la base de datos para una misma categoría?

El segundo registro de la base de datos (y, posiblemente, los siguientes) para la categoría afectada significa que ha habido actualizaciones de categoría programadas mediante el módulo Magento\_Ensayo. El módulo crea un registro adicional para una categoría en `catalog_category_entity` y ese es el comportamiento esperado de la aplicación; el problema es que los registros tienen los mismos valores para el `created_in` columna.

### ¿Cómo aparecen los mismos valores?

No podemos exponer con certeza las razones de la corrupción de datos. Las posibles razones pueden incluir:

* personalizaciones (código, temáticas, etc.)
* migración de datos incorrecta
* restauración de datos incorrecta desde la copia de seguridad

Hasta donde sabemos, estos datos dañados no son típicos de las instancias de Adobe Commerce &quot;limpias&quot; (listas para usar) y no se pueden reproducir en una instalación de Adobe Commerce sin personalizaciones.

### Comprobar si este es su problema

El `catalog_category_entity` debe tener varios registros para la categoría afectada (los registros deben tener la misma `entity_id` valor) y al menos dos de esos registros deben tener el mismo `created_in` valores. Con esto, las actualizaciones programadas de ensayo no se mostrarían en el administrador de Commerce; solo vería el bloque vacío Cambios programados.

#### Pasos a verificar

1. Acceda a la tabla catalog\_category\_entity de la base de datos.
1. Filtre las entidades por entity\_id, con entity\_id identificando la categoría afectada.
1. Si los valores de la columna created\_in son los mismos para diferentes entradas con la misma entidad\_id, ese es nuestro caso. Normalmente, la variable `created_in` Los valores de son diferentes para cada registro.

![Datos dañados en la tabla catalog_category_entity](assets/catalog_category_entity.png)

## Solución

Puede elegir una de las siguientes soluciones:

1. **Eliminar** los registros de actualización de categoría problemáticos
1. **Reparar** los registros de actualización de categoría problemáticos

### Eliminar los registros de actualización de categoría problemáticos

En esta solución, deberá configurar el correcto `updated_in` valor del registro de categoría inicial y eliminar todos los demás registros de esta categoría. Esto elimina todas las actualizaciones de categoría programadas.

Siga estos pasos:

1. Busque los registros de BD con el `entity_id` de la categoría afectada.
1. Seleccione el registro con el mayor entero de la `updated_in` columna.
1. Copie el `updated_in` del registro seleccionado.
1. Seleccione el registro con `row_id` = `entity_id` (registro de categoría inicial) y pegue el valor copiado en `updated_in` de este registro.
1. Eliminar fila(s) con `row_id` no igual a `entity_id` .

### Repare los registros de actualización de categoría problemáticos

1. Buscar los registros de categoría con el mismo `entity_id` y lo mismo `created_in` valor.
1. Seleccione el registro donde `row_id` = `entity_id` y copie el `updated_in` valor.
1. Seleccione el registro donde `row_id` is not equal to `entity_id` y pegue el `updated_in` valor como `created_in` valor. Consulte la captura de pantalla siguiente como ilustración.    ![Copiando el valor created_in.png](assets/copy_created-in_value.png)
1. Compruebe que el registro de actualización de categoría, el `created_in` cuyo valor haya actualizado (en el paso 3), existe en la variable `staging_update` tabla. *Por ejemplo:* SI el copiado `created_in` valor es 1509281953, LUEGO la entidad con `row_id` = 1509281953 debe existir en el `staging_update` tabla
