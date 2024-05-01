---
title: Varios trabajos cron programados para el mismo período de tiempo
description: Este artículo proporciona un parche para un problema conocido de Adobe Commerce 2.2.2 relacionado con la ejecución de varios trabajos cron programados al mismo tiempo después de que las variables de tiempo de determinadas tareas se editaran en el administrador de Commerce.
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Varios trabajos cron programados para el mismo período de tiempo

Este artículo proporciona un parche para un problema conocido de Adobe Commerce 2.2.2 relacionado con la ejecución de varios trabajos cron programados al mismo tiempo después de que las variables de tiempo de determinadas tareas se editaran en el administrador de Commerce.

## Problema

Cuando cron está configurado para ejecutarse cada minuto, si edita las variables de tiempo para tres tareas programadas en Admin, la variable `cron_schedule` La tabla de base de datos muestra grupos de varias tareas programadas para ejecutarse al mismo tiempo.

<u>Pasos a seguir</u>:

1. En Commerce Admin, vaya a **Tiendas** > Configuración > **Configuración** > **AVANZADO** > **Sistema** > **Cron (Tareas programadas)** > **Opciones de configuración de Cron para el grupo: predeterminado.**
1. Configure las siguientes opciones:
   * **Limpieza de historial cada**: borre el **Usar sistema** casilla de verificación y establecer en *1440*.
   * **Duración del historial de éxito**: borre el **Usar sistema** casilla de verificación y establecer en *1440*.
   * **Duración del historial de errores**: borre el **Usar sistema** casilla de verificación y establecer en *1440*.

1. Clic **Guardar configuración**.
1. En SSH, ejecute el `crontab -e` comando.
1. Configure cron para que se ejecute cada minuto.
1. Abra tres fichas/ventanas de terminal.
1. Vaya a Adobe Commerce. `root/base/project` en cada ventana de terminal.
1. Ejecute el siguiente comando en cada pestaña o ventana:

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. Vaya a MySQL y ejecute la siguiente consulta:

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. Consulte grupos de tareas programadas para ejecutarse al mismo tiempo.

<u>Resultado esperado</u>: una corona `job_code` debe programarse para el período de tiempo determinado.

<u>Resultado real</u>: Hay varios trabajos cron programados para el mismo período de tiempo.

## Solución

Para Adobe Commerce sobre comerciantes de infraestructuras en la nube, [actualización de las herramientas ECE](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) solucionará el problema.

Los comerciantes locales de Adobe Commerce deben aplicar uno de los parches adjuntos para solucionar el problema.

## Parches

Los parches se adjuntan a este artículo. Para descargar, desplácese hacia abajo hasta el final del artículo y haga clic en el nombre del archivo o haga clic en uno de los vínculos siguientes:

* [Descargar MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [Descargar MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [Descargar MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [Descargar MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [Descargar MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [Descargar MDVA-11304\_EE\_2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [Descargar MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### Versiones de Adobe Commerce compatibles

Los parches se han creado para una versión concreta indicada en el nombre del archivo de parche. Por ejemplo, MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch se creó para Adobe Commerce 2.2.4 y es el mejor parche para esta versión.

Los parches también son compatibles con las siguientes versiones:

* Para Adobe Commerce local 2.1.0-2.1.4: [Descargar MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:
   * Adobe Commerce en la infraestructura en la nube 2.1.0-2.1.4
* Para Adobe Commerce local 2.1.5-2.1.12: [Descargar MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:
   * Adobe Commerce en la infraestructura en la nube 2.1.5-2.1.12
* Para Adobe Commerce en la infraestructura en la nube 2.1.13: [Descargar MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* Para Adobe Commerce local 2.1.14-2.1.17: [Descargar MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:
   * Adobe Commerce local 2.1.18
   * Adobe Commerce en la infraestructura en la nube 2.1.14-2.1.18
* Para Adobe Commerce local 2.2.0-2.2.1: [Descargar MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:
   * Adobe Commerce en la infraestructura en la nube 2.2.0-2.2.1
* Para Adobe Commerce local 2.2.0-2.2.3: [Descargar MDVA-11304\_EE\_2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:
   * Adobe Commerce en la infraestructura en la nube 2.2.0-2.2.3
* Para Adobe Commerce local 2.2.4: [Descargar MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) El parche también es compatible (pero es posible que no resuelva el problema) con las siguientes versiones y ediciones de Adobe Commerce:
   * Adobe Commerce en la infraestructura en la nube 2.2.4

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de soporte, para obtener instrucciones.

## Archivos adjuntos
