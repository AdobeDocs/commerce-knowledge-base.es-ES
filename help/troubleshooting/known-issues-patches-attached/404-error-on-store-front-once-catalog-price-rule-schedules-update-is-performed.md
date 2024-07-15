---
title: Error 404 en la tienda una vez que se ha realizado la actualización de las programaciones de reglas de precios del catálogo
description: Este artículo proporciona un parche y los pasos necesarios para solucionar el problema conocido de Adobe Commerce 2.2.1 relacionado con la obtención de un error 404 en todas las portadas de las tiendas, después de que se creara una actualización de la regla de precios de catálogo y se editara más tarde su hora de inicio. Para solucionar el problema, debe aplicar el parche.
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Error 404 en la tienda una vez que se ha realizado la actualización de las programaciones de reglas de precios del catálogo

Este artículo proporciona un parche y los pasos necesarios para solucionar el problema conocido de Adobe Commerce 2.2.1 relacionado con la obtención de un error 404 en todas las portadas de las tiendas, después de que se creara una actualización de la regla de precios de catálogo y se editara más tarde su hora de inicio. Para solucionar el problema, debe aplicar el parche.

## Problema

Las páginas de tienda dejan de estar disponibles y devuelven el error 404. El problema aparece después de que venza la actualización de la regla de precios del catálogo activo, siempre que la fecha de inicio de esta actualización se haya editado después de la creación inicial.

<u>Pasos a seguir</u>:

1. En el administrador de Commerce, cree una nueva regla de precio de catálogo en **Marketing** > **Promociones** > **Regla de precio de catálogo**.
1. En la cuadrícula **Regla de precio de catálogo**, haz clic en **Editar,** programar una nueva actualización y establece **Estado** en *Activo.*
1. Vaya a **Contenido** > **Ensayo de contenido** > **Tablero.**
1. Seleccione la actualización creada recientemente y cambie su hora de inicio.
1. Guarde los cambios.

<u>Resultado esperado</u> :

Cuando la fecha de inicio de la actualización entra en vigor, la regla de precios del catálogo se aplica correctamente.

<u>Resultado real</u> :

Cuando la fecha de inicio de la actualización entra en vigor, todos los catálogos y productos de la tienda dejan de estar disponibles para devolver el error 404.

## Solución

Para restaurar las páginas del catálogo y poder utilizar completamente la funcionalidad de actualizaciones de las reglas de precios del catálogo, debe instalar el parche, eliminar la regla manualmente y en el administrador y corregir los vínculos no válidos en la base de datos. También deberá volver a crear la regla de precio de catálogo.

A continuación se ofrece una descripción detallada de los pasos necesarios:

1. [Aplicar el parche](#patch).
1. En el Administrador de Commerce, elimine la regla de precio de catálogo relacionada con el problema (donde se actualizó la hora de inicio). Para ello, abra la página de reglas en **Marketing** > **Promociones** > **Regla de precios de catálogo** y haga clic en **Eliminar regla**.
1. Al obtener acceso a la base de datos, se elimina manualmente el registro relacionado de la tabla `catalogrule`.
1. Corrija los vínculos no válidos en la base de datos. Consulte [párrafo relacionado](#fix_links) para obtener detalles.
1. En el Administrador de Commerce en **Marketing**, vaya a **Promociones** > **Regla de precio de catálogo** y cree la nueva regla con la configuración requerida.
1. Borre la caché del explorador en **Sistema** > **Administración de caché**.
1. Asegúrese de que los trabajos de cron estén configurados correctamente y se puedan ejecutar correctamente.

## Parche {#patch}

El parche se adjunta a este artículo. Para descargarlo, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en el siguiente vínculo:

[Descargar MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## Versiones de Adobe Commerce compatibles:

El parche se ha creado para:

* Adobe Commerce 2.2.1

El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* Adobe Commerce en infraestructura en la nube 2.2.0 - 2.2.4
* Adobe Commerce local 2.2.0 y 2.2.2 - 2.2.4

## Cómo aplicar el parche

Para obtener instrucciones, consulte [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte.

## Corregir los vínculos no válidos para ensayo en base de datos {#fix_links}

>[!WARNING]
>
>Recomendamos encarecidamente crear una copia de seguridad de la base de datos antes de cualquier manipulación de la misma. También recomendamos probar primero las consultas en el entorno de desarrollo.

Realice los siguientes pasos para corregir las filas con vínculos no válidos a la tabla `staging_update`.

1. Compruebe si los vínculos no válidos a la tabla `staging_update` existen en la tabla `flag`. Estos serían registros donde `flag_code=staging`.
1. Identifique la versión no válida de la tabla `flag` mediante la siguiente consulta:

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. En la tabla `staging_update`, seleccione la versión existente que sea menor que la versión actual (no válida) y recupere el valor de la versión que sea dos números. Lo toma, no la versión anterior, para evitar la situación en la que la versión anterior es la versión máxima de la tabla `staging_update` que se podría aplicar y aún necesitamos volver a aplicarla.

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   La versión que recibe como respuesta es su versión válida `id`.

1. Para las filas con vínculos no válidos en la tabla `flag`, establezca los valores de `flag_data` en datos que contengan un identificador de versión válido. Esto ayuda a ahorrar rendimiento en el paso de reindexación y permite evitar la reindexación de todas las entidades.

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>Ejemplo:</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## Archivos adjuntos
