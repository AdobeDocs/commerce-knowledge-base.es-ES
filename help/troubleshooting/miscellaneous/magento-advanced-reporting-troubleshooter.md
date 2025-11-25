---
title: Solucionador de problemas de informes avanzados para Adobe Commerce
description: Los problemas de informes avanzados en Adobe Commerce se pueden resolver con esta herramienta de resolución de problemas. Esto incluye Informes avanzados que no muestran datos y errores 404. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 3761e9b337ae5b3c07fb23a0bdf191b96efe55ba
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# Solucionador de problemas de informes avanzados para Adobe Commerce

Los problemas de informes avanzados en Adobe Commerce se pueden resolver con esta herramienta de resolución de problemas. Esto incluye Informes avanzados que no muestran datos y errores 404. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas.

## Paso 1: Confirmación de que el sitio cumple los requisitos avanzados de informes {#step-1}

+++**¿Cumple su sitio web con los requisitos de informes avanzados?**

Tiene una página de error 404 al usar Informes avanzados. ¿Cumple su sitio web con los [requisitos avanzados de informes](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)?

a. SÍ - Continúe con [Paso 2](#step-2).\
b. NO: complete los requisitos de informes avanzados para su sitio siguiendo los pasos de [Requisitos de informes avanzados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements). A continuación, continúe con [Paso 2](#step-2).

+++

## Paso 2: ¿Hay pedidos en varias divisas base? {#step-2}

+++**¿Se utilizan varias monedas base?**

¿Se utilizan varias divisas base (en pedidos y configuración)? Ejecute este comando [!DNL SQL] para obtener la configuración actual: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. SÍ: si la consulta devuelve varias filas, no puede usar **[!UICONTROL Advanced Reporting]**, ya que solo se admite una moneda. Tendrá que usar [Adobe Commerce Intelligence](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/guide-overview). Póngase en contacto con el equipo de su cuenta para configurar esto.
b. NO: la salida muestra solo una moneda. Ejemplo: `USD`. ¿Se han utilizado varias monedas base alguna vez (en pedidos)? Ejecute este comando [!DNL SQL] para obtener los datos del historial de pedidos:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**NOTA: este comando requiere una exploración completa de la tabla, por lo que en las tablas con un número elevado de registros, esto podría afectar al rendimiento mientras se ejecuta la consulta** para obtener datos de pedidos históricos.
Si alguna vez se han utilizado varias monedas base, no puede utilizar el sistema de informes avanzado, ya que solo se admite una moneda. Si la salida muestra solamente una moneda, continúe con [Paso 3](#step-3).

+++

## Paso 3: Comprobar si la base de datos dividida está en uso {#step-3}

+++**¿Está usando la solución de base de datos dividida?**

¿Está usando [solución de base de datos dividida](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)?

a. SÍ: use el parche **MDVA-26831** en el error de Advanced Reporting 404 en la solución de base de datos dividida y borre la caché. Espere 24 horas para que el trabajo se vuelva a ejecutar e inténtelo de nuevo.\
b. NO - Continúe con [Paso 4](#step-4).

+++

## Paso 4: Confirmar la creación de informes avanzada habilitada {#step-4}

+++**¿Se han habilitado los informes avanzados?**

Compruebe **Administración** > **Tiendas** > **Configuración** > **Configuración** > **General** > **Informes avanzados**. Para ver los pasos detallados, consulte [Informes avanzados: habilitar los informes avanzados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting).

a. SÍ - Continúe con [Paso 5](#step-5).\
b. NO - [Habilitar informes avanzados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting), guardar y esperar 24 horas a que se sincronicen Adobe Commerce y los informes avanzados. Compruebe si los datos ahora se cargan. Si es así, ha resuelto el problema. Si no continúa con [Paso 5](#step-5).

+++

## Paso 5: Comprobación del token {#step-5}

+++**¿Hay un token?**

Compruebe que haya un token ejecutando la siguiente consulta: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` ¿Hay un token?

a. SÍ - Continúe con [Paso 7](#step-7).\
b. NO: si el valor del token es NULL o no hay ningún registro en la base de datos, continúe con [Paso 6](#step-6).

+++

## Paso 6: Uso de la fila {#step-6}

+++**¿Devuelve la consulta la fila?**

Compruebe el valor del contador en la tabla de indicadores ejecutando esta consulta: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` ¿La consulta devuelve la fila?

a. SÍ - Realice los siguientes pasos: 1. Ejecute la siguiente consulta:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [Deshabilitar y habilitar el módulo de informes avanzados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) en la configuración y [volver a autorizar el token](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
3\. Espere 24 horas para que Adobe Commerce y los informes avanzados se sincronicen. Si todavía no puedes ver los datos en los informes avanzados, [envía un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO: si la consulta no devuelve nada, realice los siguientes pasos: 1. [Deshabilitar y habilitar el módulo de informes avanzados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) en la configuración y [volver a autorizar el token](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
2\. Espere 24 horas para que Adobe Commerce y los informes avanzados se sincronicen. Si todavía no puedes ver los datos en los informes avanzados, [envía un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Paso 7: Comprobación de registros en la tabla `cron_schedule` {#step-7}

+++**¿Hay registros en la tabla `cron_schedule`?**

Compruebe que se ejecutó el trabajo `analytics_collect_data` al ejecutar esta consulta: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. SÍ: si hay registros y la columna **status** indica _falta_, use el parche en este artículo de KB Actualizar informes avanzados para ejecutarse en su propio grupo cron.\
b. SÍ: si hay registros y la columna **status** indica _success_, continúe con el [paso 9](#step-9).\
c. SÍ: si hay registros y la columna **status** indica _error_, continúe con el [Paso 8.](#step-8)\
d. NO: si no hay registros, continúe con [Paso 8](#step-8).

+++

## Paso 8: Comprobación del trabajo en `support_report.log` {#step-8}

+++**¿Se inició sesión el trabajo en `support_report.log`?**

Ejecute el comando: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. SÍ: si el resultado de la consulta indica un trabajo correcto, por ejemplo `Cron Job analytics_collect_data is successfully finished`, continúe con [Paso 9](#step-9).\
b. NO: si no hay registros en el registro, [envíe un vale de soporte técnico](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. SÍ: si hay registros pero hay un error, continúe con [Paso 10](#step-10).

+++

## Paso 9: Comprobación del archivo `data.tgz` {#step-9}

+++**¿Existe el archivo `data.tgz` en el sistema y hay registros en los registros de acceso?**

Para comprobar que el archivo `data.tgz` existe, ejecute este comando; debería devolver directorios con nombres hash:

```
ls -ltr pub/media/analytics/
```

Para comprobar que hay registros en access.logs, ejecute este comando:

* En Commerce Cloud:

  ```
  zgrep -i analytics /var/log/platform/*/access.log* | grep MagentoBI
  ```

* En Local, sustituya la ruta del archivo según corresponda:
  `zgrep -i analytics <your web server's log path>/access.log* | grep MagentoBI`

a. SÍ: si el archivo `data.tgz` está presente y hay registros en los registros de acceso, pero sigue teniendo un error 404, debe [enviar un vale de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Continúe con [Paso 10](#step-10).

+++

## Paso 10: Comprobación del mensaje de error {#step-10}

+++**¿Hay un mensaje de error generado por el trabajo cron?**

Ejemplo: en la tabla `cron_schedule` se ve el error *El archivo &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0 no se puede eliminar*. Advertencia!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=en): No existe ese archivo o directorio*

a. SÍ - Usar el parche ACSD-50165 en [No se puede eliminar el archivo. Advertencia: no existe el error de archivo o directorio del administrador &#x200B;](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26887). Espere 24 horas a que el trabajo se ejecute de nuevo y vuelva a intentarlo.\
b. NO - Continúe con [Paso 11](#step-11).

+++

## Paso 11: Comprobar si hay un error de Page Builder {#step-11}

+++**¿Hay un error causado por Page Builder?**

Ejemplo: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. SÍ: utilice el parche MDVA-19391 en errores comunes de trabajos cron de informes avanzados en Adobe Commerce, espere 24 horas para que el trabajo se ejecute de nuevo e inténtelo de nuevo.\
b. NO - [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Volver al paso 1](#step-1)

## Lectura relacionada

[Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
