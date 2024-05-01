---
title: Solución de problemas de New Relic en Adobe Commerce en la infraestructura en la nube
description: Este artículo proporciona recursos para la resolución de problemas de New Relic en Adobe Commerce en la infraestructura en la nube.
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Solución de problemas de New Relic en Adobe Commerce en la infraestructura en la nube

Este artículo proporciona recursos para la resolución de problemas de New Relic en Adobe Commerce en la infraestructura en la nube.

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>Problema</strong></td>
<td class="wysiwyg-text-align-center"><strong>Causa</strong></td>
<td class="wysiwyg-text-align-center"><strong>Recursos</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problemas de acceso</td>
</tr>
<tr>
<td>
<p><u>No se pueden ver proyectos en New Relic.</u></p>
<p>Ha iniciado sesión en <em>New Relic</em> pero no puede ver proyectos a los que debería tener derecho a ver o acceder.</p>
</td>
<td>
<p>En estos casos, un usuario administrador debe agregarle al proyecto.</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html">Acceso a los servicios de New Relic</a> en nuestra base de conocimiento de soporte.</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problemas de datos</td>
</tr>
<tr>
<td>
<p><u>Faltan datos tras la instalación.</u></p>
<p>Utilice el <a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">Utilidad New Relic Diagnostics</a> para intentar identificar la causa. Si esto no ayuda, consulte las soluciones específicas del agente. Los vínculos a artículos que contienen estas soluciones se encuentran en la columna derecha.</p>
</td>
<td>
<p>La falta de datos puede tener diferentes causas. Es posible que tenga que:</p>
<ul>
<li>Compruebe que el agente está instalado.</li>
<li>Compruebe el nombre de la aplicación y la clave de licencia.</li>
<li>Reinicie el servidor web.</li>
<li>Asegúrese de que su sistema cumpla los requisitos de compatibilidad.</li>
<li>Configuración de INI.</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">Documentación de New Relic &gt; Agentes de APM &gt; No ver datos</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">Documentación de New Relic &gt; Explorador de New Relic &gt; No ver datos</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">Documentación de New Relic &gt; Infraestructura de New Relic &gt; No ver datos</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">Documentación de New Relic &gt; New Relic Mobile &gt; No se ven datos</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>Discrepancia de marca de tiempo de transacciones.</u> Es posible que tenga problemas para encontrar transacciones largas (más de 5 minutos) mediante la interfaz de usuario de New Relic. También puede encontrar transacciones mostradas fuera del lapso de tiempo esperado.</p>
</td>
<td>
<p>La interfaz de usuario de New Relic muestra la hora de finalización de la transacción, no la hora en que comenzó.</p>
</td>
<td>
<p>Para calcular el inicio de la transacción mediante la interfaz de usuario de New Relic, compruebe la duración de la transacción. Reste la cantidad de duración de la marca de tiempo (final de transacción) proporcionada por la interfaz de usuario de New Relic.</p>
</td>
</tr>
<tr>
<td>
<p><u>NerdGraph GraphQL <code>curl</code> consultas con caracteres especiales como <code>|</code> y <code>%</code> no funcionan</u>.</p>
</td>
<td>
<p>La función "copiar para rizar" de New Relic en NerdGraph actualmente no proporciona una forma de gestionar caracteres especiales como <code>|</code> y <code>%</code>.</p>
</td>
<td>
<p>Utilice una biblioteca de API diferente para resolver el problema con caracteres especiales. Por ejemplo, la biblioteca GraphQLClient para la API de Graphql en Python o Apache.commons por llamadas del lenguaje Java. Revisar bibliotecas de cliente en <a href="https://graphql.org/code/">GraphQL</a>.</p>
</td>
</tr>
<tr>
<td>
<p><u>Problemas de visualización de gráficos y paneles.</u></p>
</td>
<td>
<p>Resuelva los gráficos que faltan agregando dominios de New Relic a la lista de permitidos o desinstale la extensión del explorador que causa los problemas.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">Documentación de New Relic &gt; Faltan gráficos o no se procesan</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problemas con el agente PHP</td>
</tr>
<tr>
<td>
<p><u>El agente PHP no muestra el recuento de instancias correcto.</u></p>
</td>
<td>
<p>El número de instancias puede aumentar según los procesos back-end y el rendimiento. Las diferencias entre los valores de servidor pueden deberse a procesos que se ejecutan en un servidor, pero no en el otro.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">Documentación de New Relic &gt; Solución de problemas del recuento de instancias del agente PHP</a> </p>
</td>
</tr>
</tbody>
</table>
