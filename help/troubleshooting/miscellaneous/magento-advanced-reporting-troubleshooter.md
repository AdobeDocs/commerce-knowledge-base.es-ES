---
title: Solucionador de problemas de informes avanzados para Adobe Commerce
description: Los problemas de informes avanzados en Adobe Commerce se pueden resolver con esta herramienta de resolución de problemas. Esto incluye Informes avanzados que no muestran datos y errores 404. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Solucionador de problemas de informes avanzados para Adobe Commerce

Los problemas de informes avanzados en Adobe Commerce se pueden resolver con esta herramienta de resolución de problemas. Esto incluye Informes avanzados que no muestran datos y errores 404. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas.

## Paso 1: Confirmación de que el sitio cumple los requisitos avanzados de informes {#step-1}

+++**¿Su sitio web cumple los requisitos avanzados de creación de informes?**

Tiene una página de error 404 al usar Informes avanzados. ¿Se encuentra su sitio web? [Requisitos avanzados de informes](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements)?

a. SÍ: Continúe con [Paso 2](#step-2).\
b. NO: complete los requisitos de informes avanzados para su sitio siguiendo los pasos indicados en [Requisitos avanzados de informes](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). A continuación, continúe a [Paso 2](#step-2).

+++

## Paso 2: ¿Hay pedidos en varias divisas base? {#step-2}

+++**¿Se utilizan varias monedas base?**

¿Se utilizan varias divisas base (en pedidos y configuración)? Ejecute este comando SQL para obtener la configuración actual: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. SÍ: si la consulta devuelve varias filas, no puede utilizar los informes avanzados, ya que solo se admite una moneda.\
b. NO: la salida muestra solo una moneda. Ejemplo: `USD`. ¿Se han utilizado varias monedas base alguna vez (en pedidos)? Ejecute este comando SQL para obtener los datos de pedidos históricos:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**NOTA: Este comando requiere una exploración completa de la tabla, por lo que para las tablas con un gran número de registros, esto podría afectar al rendimiento mientras se ejecuta la consulta** para obtener datos de pedidos históricos.
Si alguna vez se han utilizado varias monedas base, no puede utilizar el sistema de informes avanzado, ya que solo se admite una moneda. Si la salida muestra solo una moneda, proceda a [Paso 3](#step-3).

+++

## Paso 3: Comprobar si la base de datos dividida está en uso {#step-3}

+++**¿Está utilizando la solución de base de datos dividida?**

¿Está utilizando [solución de base de datos dividida](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html)?

a. SÍ - Utilice el parche **MDVA-26831** in [Error de Advanced Reporting 404 en la solución de base de datos dividida](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) y borre la caché. Espere 24 horas para que el trabajo se vuelva a ejecutar e inténtelo de nuevo.\
b. NO: Continúe con [Paso 4](#step-4).

+++

## Paso 4: Confirmar la creación de informes avanzada habilitada {#step-4}

+++**¿Está habilitado el sistema de informes avanzado?**

Marque **Administrador** > **Tiendas** > **Configuración** > **Configuración** > **General** > **Avanzadas**. Para ver los pasos detallados, consulte [Informes avanzados: Habilitar informes avanzados](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a. SÍ: Continúe con [Paso 5](#step-5).\
b. NO - [Habilitar informes avanzados](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) , guarde y espere 24 horas a que se sincronicen Adobe Commerce y Advanced Reporting. Compruebe si los datos ahora se cargan. Si es así, ha resuelto el problema. Si no procede, vaya a [Paso 5](#step-5).

+++

## Paso 5: Comprobación del token {#step-5}

+++**¿Hay un token?**

Compruebe que haya un token ejecutando la siguiente consulta: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` ¿Hay un token?

a. SÍ: Continúe con [Paso 7](#step-7).\
b. NO: si el valor del token es NULL o no hay ningún registro en la base de datos, continúe a [Paso 6](#step-6).

+++

## Paso 6: Uso de la fila {#step-6}

+++**¿Devuelve la consulta la fila?**

Compruebe el valor del contador en la tabla de indicadores ejecutando esta consulta: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` ¿Devuelve la consulta la fila?

a. SÍ - Realice los siguientes pasos: 1. Ejecute la siguiente consulta:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [Deshabilitar y habilitar el módulo de informes avanzados](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) en configuración y [volver a autorizar el token](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3\. Espere 24 horas para que Adobe Commerce y los informes avanzados se sincronicen. Si sigue sin poder ver los datos en Informes avanzados, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO: si la consulta no devuelve nada, realice los siguientes pasos: 1. [Deshabilitar y habilitar el módulo de informes avanzados](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) en configuración y [volver a autorizar el token](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\. Espere 24 horas para que Adobe Commerce y los informes avanzados se sincronicen. Si sigue sin poder ver los datos en Informes avanzados, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Paso 7: Comprobación de registros en `cron_schedule` tabla {#step-7}

+++**¿Hay registros en el `cron_schedule` ¿mesa?**

Compruebe ese trabajo `analytics_collect_data` se ejecutó ejecutando esta consulta: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. SÍ: si hay registros y la variable **status** la columna dice _pasado por alto_, use el parche en este artículo de KB [Actualice los informes avanzados para que se ejecuten en su propio grupo cron](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b. SÍ: si hay registros y la variable **status** la columna dice _success_, continúe a [Paso 9](#step-9).\
c. SÍ - Si hay registros y la **status** la columna dice _error_, continúe a [Paso 8.](#step-8)\
d. NO: si no hay registros, continúe a [Paso 8](#step-8).

+++

## Paso 8: Comprobación del trabajo en `support_report.log` {#step-8}

+++**Se ha iniciado sesión en el trabajo `support_report.log`?**

Ejecute el comando: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. SÍ: si el resultado de la consulta indica un trabajo correcto, por ejemplo, `Cron Job analytics_collect_data is successfully finished` proceda a [Paso 9](#step-9).\
b. NO: si no hay registros en el registro, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. SÍ: si hay registros pero hay un error, proceda a [Paso 10](#step-10).

+++

## Paso 9: Comprobación de `data.tgz` archivo {#step-9}

+++**¿El archivo `data.tgz` existen en el sistema y hay registros en los registros de acceso?**

Para comprobar que el archivo `data.tgz` existe, ejecute el comando:

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

Para comprobar que hay registros en access.logs, ejecute el comando:

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. SÍ - Si el archivo `data.tgz` está presente y hay registros en los registros de acceso, pero aun así tiene un error 404, debe [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO: Continúe con [Paso 10](#step-10).

+++

## Paso 10: Comprobación del mensaje de error {#step-10}

+++**¿El trabajo cron genera un mensaje de error?**

Ejemplo: En el `core_config_data` tabla en la que se ve el error *El archivo &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot; no se puede eliminar*. Advertencia!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=en): No existe ese archivo o directorio*

a. SÍ - Utilice el parche ACSD-50165 en [El archivo no se puede eliminar. Advertencia: no existe el error de archivo o directorio del administrador.](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), espere 24 horas a que el trabajo se ejecute de nuevo y vuelva a intentarlo.\
b. NO: Continúe con [Paso 11](#step-11).

+++

## Paso 11: Comprobar si hay un error de Page Builder {#step-11}

+++**¿Hay un error causado por Page Builder?**

Ejemplo: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. SÍ - Uso del parche MDVA-19391 en [Errores de trabajo cron comunes de informes avanzados en Adobe Commerce](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md), espere 24 horas a que el trabajo se ejecute de nuevo e inténtelo de nuevo.\
b. NO - [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Volver al paso 1](#step-1)
