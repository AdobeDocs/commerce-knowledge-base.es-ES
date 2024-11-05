---
title: Solucionador de problemas de caída del sitio Adobe Commerce
description: Haga clic en cada pregunta para mostrar los detalles de la respuesta en cada paso del solucionador de problemas.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# Solucionador de problemas de caída del sitio Adobe Commerce

Haga clic en cada pregunta para mostrar los detalles de la respuesta en cada paso del solucionador de problemas.

## Paso 1 {#step-1}

+++**¿Muestra <https://status.adobe.com> algún problema?**

a. SÍ: si comprobó [Adobe Commerce Status](https://status.adobe.com/cloud/experience_cloud) y se mostró un problema, abra un [ticket de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para investigar más a fondo.\
b. NO: si comprobó [Adobe Commerce Status](https://status.adobe.com/cloud/experience_cloud) y no se mostró ningún problema, continúe con el [Paso 2](#step-2).

+++

## Paso 2 {#step-2}

+++**¿Muestra http://status.fastly.com algún problema?**

a. SÍ: si comprobó [[!DNL Fastly] Status](https://status.fastly.com/) y se mostró un problema, abra un [ticket de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para realizar una investigación más a fondo.\
b. NO: si comprobó [[!DNL Fastly] Status](https://status.fastly.com/) y no se mostró ningún problema, continúe con el [Paso 3](#step-3).

+++

## Paso 3 {#step-3}

+++**Compruebe su sitio web en un explorador web. ¿Obtiene un código 200 (OK)?**

Para comprobar los códigos de error en **Firefox**: Haz clic en el icono de **Abrir menú** > **Desarrollador web** > **Alternar herramientas** > **Red** pestaña > **Todo** filtro > **Estado** columna. Para comprobar los códigos de error en **Chrome**: Haz clic en el icono de **Abrir menú** > **Más herramientas** > **Herramientas para desarrolladores** > **Red** pestaña > **Todo** filtro > **Estado** columna.

a. SÍ: abre un [ticket de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para una investigación más detallada.\
b. NO - Continúe con [Paso 4](#step-4).

+++

## Paso 4 {#step-4}

+++**¿Qué código de error de sitio web recibió?**

a. Código de error 500 - Registro de comprobación de `/var/log/platform/`. Si estos datos no le presentan el problema, puede abrir un [vale de soporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) e incluir la información de solución de problemas que tiene hasta el momento para una mayor investigación.

b. Código de error 503 - Registro de comprobación de `var/reports`. Si estos datos no le presentan el problema, puede abrir un [vale de soporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) e incluir la información de solución de problemas que tiene hasta el momento para una mayor investigación.

c. Código de error 404 - Ejecute la siguiente consulta: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Si la consulta devuelve una tabla, donde el valor de `update_exists` es &quot;0&quot;, consulte el [Error 404 en todas las páginas, tienda y administrador, debido a un problema con el almacenamiento provisional de contenido](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue) artículo. En todos los demás casos, continúe con [Paso 5](#step-5).

d. Otros códigos de error - Continúe con [Paso 5](#step-5).

+++

## Paso 5 {#step-5}

+++**¿Su sitio es lento o tiene una carga de servidor alta, una carga de CPU alta, un procesamiento de solicitudes lento o interrupciones en [!DNL MySQL] o Redis?**

a. SÍ - Continúe con los pasos para [Comprobar ataques DDOS de CLI](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli).\
b. NO: compruebe los registros de `/var/log/exception.log` y `/var/log/deploy.log` y, si estos datos no le presentan el problema, continúe con [Paso 6](#step-6).

+++

## Paso 6 {#step-6}

+++**¿Tiene errores o errores de implementación?**

a. SÍ - Continúe con [Paso 13](#step-13).\
b. NO - Continúe con [Paso 7](#step-7).

+++

## Paso 7 {#step-7}

+++**¿Tiene errores de Elasticsearch?**

a. SÍ - Continúe con los pasos para [comprobar el Elasticsearch](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch/).\
b. NO - Continúe con [Paso 8](#step-8).

+++

## Paso 8 {#step-8}

+++**¿Tenía su base de datos [!DNL MySQL] consultas lentas o incorrectas?**

a. SÍ: continuar con [Comprobando consultas y procesos lentos que tardan demasiado en [!DNL MySQL]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) and checking your query structure in this [[!DNL MySQL] tutorial de consultas](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO - Continúe con [Paso 9](#step-9).

+++

## Paso 9 {#step-9}

+++**¿No está disponible tu contenido estático?**

a. SÍ - Continúe consultando el artículo [Comprobando contenido estático](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment).\
b. NO - Continúe con [Paso 10](#step-10).

+++

## Paso 10 {#step-10}

+++**¿Ve errores graves de PHP en sus registros?**

a. SÍ - Continúe consultando [Errores y soluciones comunes de PHP](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions).\
b. NO - Continúe con [Paso 11](#step-11).

+++

## Paso 11 {#step-11}

+++**¿Está viendo errores de Redis?**

a. SÍ - Continúe con los pasos para [comprobar [!DNL Redis] que se está ejecutando](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/redis#troubleshooting-redis) y para [[!DNL Redis] solucionar problemas](https://redis.io/topics/problems).\
b. NO - Continúe con [Paso 12](#step-12).

+++

## Paso 12 {#step-12}

+++**¿Está viendo errores de indizador?**

a. SÍ: si el índice está bloqueado por otro proceso, consulte [El índice está bloqueado por otro proceso](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/index-is-locked-by-another-process). Si tiene otros errores de indizador, abra un [vale de soporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para una investigación más detallada.\
b. NO - Abra un [ticket de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para realizar una investigación más a fondo.

+++

## Paso 13 {#step-13}

+++**¿Tiene problemas con sus módulos personalizados?**

a. SÍ - Continúe consultando la [Ayuda general para la solución de problemas del módulo personalizado](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help).\
b. NO - Continúe con [Paso 14](#step-14).

+++

## Paso 14 {#step-14}

+++**¿Tiene errores posteriores al enlace?**

a. SÍ: continúe comprobando el error [!DNL MySQL] en esta [[!DNL MySQL] referencia de mensaje de error del servidor](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Continúe con [Paso 15](#step-15).

+++

## Paso 15 {#step-15}

+++**¿Tiene problemas con los parches del compositor?**

a. SÍ - Continúe con la consulta [Al aplicar un parche, el sitio deja de funcionar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down).\
b. NO - Continúe con [Paso 16](#step-16).

+++

## Paso 16 {#step-16}

+++**¿Tiene errores de base de datos SQL?**

a. SÍ: continúe comprobando el error [!DNL MySQL] en esta [[!DNL MySQL] referencia de mensaje de error del servidor](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Continúe con [Paso 17](#step-17).

+++

## Paso 17 {#step-17}

+++**¿Tiene [!DNL MySQL] interbloqueos de base de datos o una base de datos [!DNL MySQL] que no responde?**

a. SÍ: continuar con la comprobación de [!DNL MySQL] interbloqueos en este artículo de [interbloqueos en [!DNL MySQL]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/deadlocks-in-mysql).\
b. NO - Abra un [ticket de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) para realizar una investigación más a fondo.

+++

[Volver al paso 1](#step-1)

Haga clic [AQUÍ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram) para ver el diagrama de flujo de solución de problemas de localización descendente.

## Lectura relacionada

[Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
