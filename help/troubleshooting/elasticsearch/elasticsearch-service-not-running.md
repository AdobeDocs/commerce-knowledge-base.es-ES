---
title: El servicio Elasticsearch no se está ejecutando
description: Este artículo proporciona soluciones para los errores que puede experimentar cuando el servicio Elasticsearch (ES) no se está ejecutando (normalmente como resultado de un bloqueo). Los síntomas pueden incluir errores al ejecutar las comprobaciones de estado utilizando curl, reindexación mediante la línea de comandos, errores de excepción y PHP y errores en las páginas de productos. En la tabla se enumeran los errores y los vínculos a los recursos para intentar resolverlos. Un síntoma puede tener una serie de causas diferentes.
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# El servicio Elasticsearch no se está ejecutando

Este artículo proporciona soluciones para los errores que puede experimentar cuando el servicio Elasticsearch (ES) no se está ejecutando (normalmente como resultado de un bloqueo). Los síntomas pueden incluir errores al ejecutar las comprobaciones de estado utilizando curl, reindexación mediante la línea de comandos, errores de excepción y PHP y errores en las páginas de productos. En la tabla se enumeran los errores y los vínculos a los recursos para intentar resolverlos. Un síntoma puede tener una serie de causas diferentes.

## Compatibilidad de la versión del Elasticsearch con Adobe Commerce

* Adobe Commerce local y Adobe Commerce en la infraestructura en la nube:

   * v2.2.3+ es compatible con ES 5.x
   * v2.2.8+ y v2.3.1+ admiten ES 6.x
   * No se recomienda las versiones 2.x y 5.x de ES debido a [fin de vida útil](https://www.elastic.co/support/eol). Sin embargo, si tienes Adobe Commerce v2.3.1 y quieres usar ES 2.x o ES 5.x, debes [Cambiar el Elasticsearch php Client](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

* Magento Open Source v2.3.0+ es compatible con ES 5.x y 6.x (pero se recomienda 6.x).

<table>
<tr>
<th>Síntomas cuando el servicio ES no se está ejecutando</th>
<th>Detalles</th>
<th>Recursos</th>
</tr>
<tr>
<td rowspan="3">Errores de excepción</td>
</tr>
<tr>
<td>
<code>{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}]</code>
</td>
<td>
El Elasticsearch <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html">5 está configurado, pero la página de búsqueda no se carga con el error "Los datos de campo están deshabilitados..." </a> en nuestra base de conocimiento de soporte.
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
No se eliminan los índices de Elasticsuite.  Ver los índices de seguimiento de <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">ElasticSuite causa problemas con el Elasticsearch</a> en nuestra base de conocimiento de soporte.
 </td>
</tr>
<tr>
<td>Error de PHP</td>
<td>
<i>No se encontraron nodos activos en su clúster","1":"#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>Recursos para espacio en disco insuficiente:<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">8 consejos para resolver los problemas del disco duro de los sistemas Linux y Unix como el disco lleno o no puede escribir en el disco</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">error del servidor: df dice que el disco está lleno, pero no lo está</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com: ¿Rastreando dónde se ha ido el espacio en disco en Linux?</a></li>
<li>Los archivos de registro no se archivan con la regularidad suficiente. Consulte <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/systems/action-logs/action-log-archive">Configurar el archivo de registro</a> en nuestra documentación para desarrolladores.</li>
<li>Los directorios del sistema de archivos no están optimizados. Consulte <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#resource-file-optimization">Optimización de archivos</a> en nuestra documentación para desarrolladores.</li>
<li>Si las soluciones de la documentación anterior no resuelven el problema, póngase en contacto con el equipo de cuenta de Adobe de para solicitar almacenamiento adicional.</li>
</ul>
</li>
<li>Si el disco no se ha quedado sin almacenamiento, pero sigue recibiendo mensajes de error en la columna izquierda, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">envíe un ticket de asistencia</a>.</li>
</ul>
<ul>
<li>Ver los índices de seguimiento de <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">ElasticSuite causa problemas con el Elasticsearch</a> en nuestra base de conocimiento de soporte.
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> error</td>
<td>La ejecución del comando <code>curl</code> para comprobar el estado del Elasticsearch:<code>curl -m1 localhost:9200/_cluster/health?pretty</code>(o<code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code>para cuentas de inicio) produce este error: <i>Error: curl: (7) No se pudo conectar al puerto localhost 9200: Conexión rechazada</i> </td>
</tr>
<tr>
<td>Error de la línea de comandos</td>
<td>La ejecución de <code>$ bin/magento indexer:reindex catalogsearch_fulltext</code> produce este error <i>Error desconocido en el proceso del indizador de búsqueda en el catálogo:
        No se encontraron nodos activos en su clúster</i>
</td>
</tr>
<tr>
<td>Error en las páginas del producto
</td>
<td><i>Se ha producido un error al procesar su solicitud.
      La impresión de excepciones está desactivada de forma predeterminada por motivos de seguridad</code></i>
</tr>
</table>
