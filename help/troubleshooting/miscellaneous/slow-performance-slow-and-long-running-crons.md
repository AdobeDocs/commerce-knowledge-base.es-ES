---
title: Lento rendimiento, crons lentos y de larga duración
description: Este artículo describe cómo resolver los problemas de rendimiento del sitio y la ejecución lenta y los crones atascados causados por la activación de tablas planas e indexadores.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Lento rendimiento, crons lentos y de larga duración

>[!WARNING]
>
>En cualquier versión de Adobe Commerce, ya que algunas extensiones solo funcionan con tablas planas, existe el riesgo de que se deshabiliten las tablas planas. Si sabe que tiene algunas extensiones que utilizan indexadores de catálogo plano, puede que tenga que tenerlo en cuenta al configurar esos valores en &quot; *No* &quot;.

Este artículo describe cómo resolver los problemas de rendimiento del sitio y la ejecución lenta y los crones atascados causados por [tablas planas e indexadores](https://docs.magento.com/m2/ce/user_guide/catalog/catalog-flat.html) se ha habilitado.

PRODUCTOS Y VERSIONES AFECTADOS

* Adobe Commerce en la infraestructura en la nube 2.1.x y superior
* Adobe Commerce local 2.1.x y superior
* Magento Open Source 2.1.x y superior

## Problema

Los indexadores planos pueden causar:

* Problemas de rendimiento del sitio y carga SQL pesada.
* Larga carrera y crones atascados.

## Causa

Tablas planas e indexadores activados.

## Solución {#solution}

A partir de Adobe Commerce y Magento Open Source 2.1.x y versiones posteriores, el uso de un catálogo plano ya no es una práctica recomendada y no se recomienda. Se sabe que el uso continuo de esta función causa una degradación del rendimiento y otros problemas de indexación. Para desactivar el catálogo plano:

1. En el Administrador, vaya a **Tiendas** > **Configuración** > **Configuración**.
1. En el panel de la izquierda debajo de **Catálogo** , elija **Catálogo**.
1. Expanda el **Tienda** y haga lo siguiente:
   * Establecer **Utilizar categoría de catálogo plano** hasta *No*.
   * Establecer **Usar producto de catálogo plano** hasta *No*.
1. Cuando termine, haga clic en **Guardar configuración**. A continuación, cuando se le solicite, actualice la caché.
1. Vaciar la caché ejecutando `php bin/magento cache:flush`.

Si no puede cambiar el **Utilizar categoría de catálogo plano** y **Usar producto de catálogo plano** hasta *No* como las opciones están atenuadas, deshabilite los indexadores planos en `app/etc/config.php`:

1. Ejecute este comando para asegurarse de que todos los indexadores están configurados en Actualizar según la programación: `php bin/magento indexer:set-mode schedule`.
1. Editar `app/etc/config.php` y busque las líneas con `flat_catalog_product` y `flat_catalog_category` - cambie de 1 a 0 para deshabilitarlos.
1. Ejecute el comando `php bin/magento app:config:import`
1. Ejecute este comando para confirmar que los indexadores planos están desactivados: `php        bin/magento indexer:status`.
1. Vaciar la caché ejecutando `php bin/magento cache:flush`.

## Información relacionada

[Restablecer manualmente los trabajos cron de Adobe Commerce atascados en la nube](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) en nuestra base de conocimiento de soporte.
