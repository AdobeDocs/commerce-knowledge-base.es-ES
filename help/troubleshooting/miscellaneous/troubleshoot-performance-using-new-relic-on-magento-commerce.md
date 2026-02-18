---
title: Solución de problemas de rendimiento con New Relic en Adobe Commerce
description: 'Este artículo proporciona pasos de solución de problemas para resolver los problemas de rendimiento de Adobe Commerce en la infraestructura en la nube mediante New Relic. También proporciona recursos para obtener más información. Esta es una lista de problemas. Haga clic para ver los pasos de solución de problemas en nuestra base de conocimiento de asistencia:'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Solución de problemas de rendimiento con New Relic en Adobe Commerce

Este artículo proporciona pasos de solución de problemas para resolver los problemas de rendimiento de Adobe Commerce en la infraestructura en la nube mediante New Relic. También proporciona recursos para obtener más información. Los siguientes problemas cubiertos en la siguiente tabla con recursos recomendados son:

* Puntuación Apdex baja
* Alto uso de CPU
* Operaciones de E/S alta
* Interrupción

<table>
<tbody>
<tr>
<td>Problema</td>
<td>Resolución de problemas</td>
<td>Recursos</td>
</tr>
<tr>
<td>
<p>Puntuación Apdex baja:</p>
<p>Su puntuación de New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Apdex</a> mide la satisfacción de los usuarios con el tiempo de respuesta de sus aplicaciones y servicios web.</p>
</td>
<td>
<p>Inicia sesión en <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Información general. A la derecha de la página Información general, verá el gráfico de puntuación de Apdex. Una puntuación de Apdex de 0,5 o menos es motivo de preocupación y merece una investigación: Tiempos de transacción web (solicitudes del servidor):</p>
<ol>
<ol>
<li>Inicie sesión en <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (seleccione una aplicación) &gt; Información general. Asegúrese de que el filtro está establecido en Tiempo de transacciones web en el filtro desplegable del gráfico principal. A continuación, en la tabla Transacciones, busque Hora del servidor de aplicaciones. Compruebe si tiene transacciones sospechosas o de larga duración.</li>
<li>Investigue cada uno de ellos de forma individual en Supervisión &gt; Transacciones y asegúrese de establecer los filtros para Web y Más tiempo<em>.</em>
</li>
<li>A continuación, busque módulos de terceros que consuman recursos: proveedores de pagos, ERP, etc.</li>
<li>En la sección Monitorización de APM:<ol>
<li>Haga clic en Transacciones.</li>
<li>Desplácese hacia abajo y haga clic en Mostrar todas las tablas de transacciones.</li>
<li>Puede ordenar transacciones por <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">varios parámetros</a> y saltar a los que causan sospechas.</li>
<li>Revise las transacciones con una puntuación Apdex baja, una cantidad de tiempo medio inusualmente alta o un porcentaje de rechazo.</li>
<li>Haga clic en cada transacción individual. Si no puede resolver el problema, <a href="https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket">envíe un vale de soporte técnico.</a>
</li>
<li>Si necesita investigar más a fondo, considere la posibilidad de comprobar las transacciones que no sean de web.</li>
</ol>
</li>
</ol>
</ol>
<p>Tiempo de transacción no web (operaciones y tareas en segundo plano):</p>
<ol>
<ol>
<li>Inicie sesión en <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (seleccione una aplicación) &gt; Información general. Asegúrese de seleccionar Tiempo de transacciones no web en el filtro desplegable del gráfico principal. Pulse en transacciones individuales de la tabla Transacciones. Busque transacciones sospechosas o de larga duración. Esto incluye trabajos back-end, trabajos cron o trabajos de importación/exportación, incluidos los de terceros.</li>
</ol>
</ol>
</td>
<td>
<p>Para obtener más información sobre la puntuación de New Relic Apdex, consulte <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">Documentación de New Relic &gt; APM Apdex &gt; Medir la satisfacción del usuario</a>. También puede consultar <a href="https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-apdex-warning-alert">Alertas administradas para Adobe Commerce: Apdex warning alert</a> en nuestra base de conocimiento de asistencia.</p>
</td>
</tr>
<tr>
<td>
<p>Alto uso de CPU:</p>
<p>Un uso elevado de CPU puede indicar que hay un servicio especialmente ocupado, como MySQL, Redis, etc.</p>
</td>
<td>
<ol>
<li>Inicie sesión en <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infraestructura &gt; Procesos.</li>
<li>Revise los gráficos de CPU para ver si hay algún proceso atascado o de alto consumo que esté usando más del 100 % del tiempo de CPU y compárelo con el recuento de procesadores de la instancia. Preste atención a los picos en la utilización de los recursos. No se recomienda matar un proceso a menos que sea un cron atascado.</li>
</ol>
</td>
<td>
<p>Para obtener más información sobre las métricas de rendimiento, en particular el porcentaje de CPU, los bytes de E/S y el uso de memoria para procesos individuales o en grupos, consulte <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">Documentación de New Relic &gt; Página de IU de infraestructura &gt; Página de host de infraestructura &gt; Pestaña Procesos</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Operaciones de E/S altas: Para cada cliente, este número es individual, pero es significativamente diferente de la media.</p>
</td>
<td>
<p>Busque un pico inusual en comparación con el promedio de operaciones de E/S anteriores:</p>
<ol>
<li>Inicie sesión en <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infraestructura &gt; Procesos.</li>
<li>Revise el gráfico Bytes leídos de E/S por segundo.</li>
<li>Registre la hora del pico.</li>
<li>Haga clic en APM.</li>
<li>Asegúrese de seleccionar el tiempo de las transacciones web en el filtro desplegable del gráfico principal.</li>
<li>Establezca la hora para la hora del pico que ha registrado.</li>
<li>Busque transacciones que hayan causado operaciones de E/S altas.</li>
<li>Desglóselo en cada Seguimiento de transacciones &gt; Detalles de seguimiento para encontrar lo que podría estar causando problemas.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>Interrupción: New Relic determina las interrupciones por Apdex. Verá una línea roja en el gráfico de puntuación de Apdex, que indica Apdex &lt; 0,4, lo que se considera una interrupción del servicio.</p>
</td>
<td>
<p>La investigación de una interrupción puede llevar a cabo varios pasos, examinando las transacciones web y no web, las bases de datos y las transacciones de terceros. Transacciones web:</p>
<ol>
<li>Inicie sesión en <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Información general. Asegúrese de que el filtro está establecido en Tiempo de transacciones web en el filtro de gráfico desplegable.</li>
<li>Reduzca manualmente la ventana de tiempo.</li>
<li>Haga clic en Transacciones. Asegúrese de que los filtros están configurados en Web y en Más tiempo. Investigue la transacción de más larga duración.</li>
<li>Si necesita investigar más a fondo, considere la posibilidad de comprobar las transacciones que no sean de web.</li>
</ol>
<p>Transacciones no web:</p>
<ol>
<li>Vuelva a la página Información general y cambie a Transacciones no web en el filtro desplegable.</li>
<li>Revise los seguimientos de transacciones en la parte inferior de la página, uno por uno.</li>
<li>Según el problema, es posible que necesite utilizar una herramienta de terceros como un generador de perfiles PHP para encontrar un cuello de botella.</li>
<li>Si necesita investigar más a fondo, considere examinar los procesos de la base de datos.</li>
</ol>
<p>Procesos de base de datos:</p>
<ol>
<li>En la página de APM, vaya a Monitoring &gt; Databases.</li>
<li>Ordenar por Más tiempo.</li>
<li>Revise las consultas TOP.

Nota: <code>ACTUALIZACIÓN</code> o <code>INSERT</code>Las consultas son las consultas que más consumen CPU.</li>
<li>Cambie a Rendimiento desde Ordenar por selector y busque los procesos que han causado que el rendimiento de la base de datos se despliegue.</li>
<li>Si necesita investigar más a fondo, considere examinar los servicios de terceros.</li>
</ol>
<p>Servicios de terceros:</p>
<ol>
<li>En la página de APM, vaya a Monitoring &gt; External services.</li>
<li>Seleccione el Tiempo de respuesta promedio más lento de la lista desplegable Ordenar por.</li>
<li>Busque los procesos que se produjeron justo antes de la interrupción.</li>
</ol>
</td>
<td>
<p>Para obtener más información sobre cómo investigar problemas de rendimiento específicos, consulte <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">Documentación de New Relic &gt; Páginas de la interfaz de usuario de APM &gt; Página de transacciones &gt; Usar funciones de desglose</a>.</p>
</td>
</tr>
</tbody>
</table>
