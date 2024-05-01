---
title: Solucionador de problemas de caída del sitio Adobe Commerce
description: Haga clic en cada pregunta para mostrar los detalles de la respuesta en cada paso del solucionador de problemas.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Solucionador de problemas de caída del sitio Adobe Commerce

Haga clic en cada pregunta para mostrar los detalles de la respuesta en cada paso del solucionador de problemas.

## Paso 1 {#step-1}

+++**Does <https://status.adobe.com> ¿mostrar algún problema?**

a. SÍ: si ha marcado [Estado del Magento de Adobe](https://status.adobe.com/products/3350) y mostraba un problema, abra una [Ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para una investigación posterior.\
b. NO - Si ha marcado [Estado del Magento de Adobe](https://status.adobe.com/products/3350) y no mostraba ningún problema, proceda a [Paso 2](#step-2).

+++

## Paso 2 {#step-2}

+++**¿Muestra http://status.fastly.com algún problema?**

a. SÍ: si ha marcado [Estado rápido](https://status.fastly.com/) y mostraba un problema, abra una [Ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para una investigación posterior.\
b. NO - Si ha marcado [Estado rápido](https://status.fastly.com/) y no mostraba ningún problema, proceda a [Paso 3](#step-3).

+++

## Paso 3 {#step-3}

+++**Compruebe el sitio web en un explorador web. ¿Recibe un código 200 (OK)?**

Para comprobar los códigos de error en **Firefox**: haga clic en **Abrir menú** icono > **Desarrollador web** > **Alternar herramientas** > **Red** pestaña > **Todo** filtrar > **Estado** columna. Para comprobar los códigos de error en **Chrome**: haga clic en **Abrir menú** icono > **Más herramientas** > **Herramientas para desarrolladores** > **Red** pestaña > **Todo** filtrar > **Estado** columna.

a. SÍ - Abrir una [Ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para una investigación posterior.\
b. NO: Continúe con [Paso 4](#step-4).

+++

## Paso 4 {#step-4}

+++**¿Qué código de error de sitio web recibió?**

a. Código de error 500: compruebe el registro de `/var/log/platform/`. Si estos datos no le presentan el problema, puede abrir un [Ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e incluya la información de solución de problemas que tiene hasta el momento para una investigación más detallada.

b. Código de error 503 - Registro de comprobación de `var/reports`. Si estos datos no le presentan el problema, puede abrir un [Ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e incluya la información de solución de problemas que tiene hasta el momento para una investigación más detallada.

c. Código de error 404: ejecute la siguiente consulta: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Si la consulta devuelve una tabla, donde `update_exists` el valor es &quot;0&quot;, consulte la [Error 404 en todas las páginas, tienda y administrador, debido a un problema con el ensayo de contenido](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md) artículo. En todos los demás casos, proceda a [Paso 5](#step-5).

d. Otros códigos de error: Continúe con [Paso 5](#step-5).

+++

## Paso 5 {#step-5}

+++**¿Su sitio es lento o tiene una carga de servidor alta, una carga de CPU alta, un procesamiento de solicitudes lento o interrupciones en MySQL o Redis?**

a. SÍ: Continúe con los pasos para [Comprobación de ataques DDOS desde CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md).\
b. NO: comprobar los registros de `/var/log/exception.log` y `/var/log/deploy.log`, y si estos datos no le plantean el problema, continúe a [Paso 6](#step-6).

+++

## Paso 6 {#step-6}

+++**¿Tiene errores de implementación o de implementación?**

a. SÍ: Continúe con [Paso 13](#step-13).\
b. NO: Continúe con [Paso 7](#step-7).

+++

## Paso 7 {#step-7}

+++**¿Tiene errores de Elasticsearch?**

a. SÍ: Continúe con los pasos para [Elasticsearch verificador](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html).\
b. NO: Continúe con [Paso 8](#step-8).

+++

## Paso 8 {#step-8}

+++**¿Tenía la base de datos MySQL consultas lentas o incorrectas?**

a. SÍ: continuar con [Comprobación de consultas y procesos lentos que tardan demasiado en MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) y comprobando la estructura de consultas en esta [Tutorial de consultas MySQL](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO: Continúe con [Paso 9](#step-9).

+++

## Paso 9 {#step-9}

+++**¿El contenido estático no está disponible?**

a. SÍ - Continúe consultando al [Comprobación de contenido estático](https://support.magento.com/hc/en-us/articles/360031624091) artículo.\
b. NO: Continúe con [Paso 10](#step-10).

+++

## Paso 10 {#step-10}

+++**¿Ve errores graves de PHP en sus registros?**

a. SÍ - Proceder a la consulta [Errores y soluciones mortales comunes de PHP](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md).\
b. NO: Continúe con [Paso 11](#step-11).

+++

## Paso 11 {#step-11}

+++**¿Está viendo errores de Redis?**

a. SÍ: Continúe con los pasos para [Verificar que Redis se esté ejecutando](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) y para [Solución de problemas de Redis](https://redis.io/topics/problems).\
b. NO: Continúe con [Paso 12](#step-12).

+++

## Paso 12 {#step-12}

+++**¿Está viendo errores de indizador?**

a. SÍ: si el índice está bloqueado por otro proceso, consulte [El índice está bloqueado por otro proceso](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). Si tiene otros errores de indizador, abra un [Ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para una investigación posterior.\
b. NO - Abra un [Ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para una investigación posterior.

+++

## Paso 13 {#step-13}

+++**¿Tiene problemas con sus módulos personalizados?**

a. SÍ - Proceder a la consulta [Ayuda general sobre solución de problemas del módulo personalizado](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b. NO: Continúe con [Paso 14](#step-14).

+++

## Paso 14 {#step-14}

+++**¿Tiene errores post-gancho?**

a. SÍ: continúe comprobando el error de MySQL en esta [Referencia de mensaje de error de servidor MySQL](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO: Continúe con [Paso 15](#step-15).

+++

## Paso 15 {#step-15}

+++**¿Tiene problemas con los parches del compositor?**

a. SÍ - Proceder a la consulta [La aplicación de un parche desactiva el sitio](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. NO: Continúe con [Paso 16](#step-16).

+++

## Paso 16 {#step-16}

+++**¿Tiene errores de base de datos SQL?**

a. SÍ: continúe comprobando el error de MySQL en esta [Referencia de mensaje de error de servidor MySQL](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO: Continúe con [Paso 17](#step-17).

+++

## Paso 17 {#step-17}

+++**¿Tiene interbloqueos de la base de datos MySQL o una base de datos MySQL que no responde?**

a. SÍ: continúe comprobando si hay interbloqueos MySQL en esto [Interbloqueos en MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md) artículo.\
b. NO - Abra un [Ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para una investigación posterior.

+++

[Volver al paso 1](#step-1)

Clic [AQUÍ](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) para ver el diagrama de flujo de solución de problemas de caída del sitio.
