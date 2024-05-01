---
title: El motor de búsqueda del catálogo MySQL se eliminará en Adobe Commerce 2.4.0
description: Adobe Commerce local, Adobe Commerce en la infraestructura en la nube y Magento Open Source 2.4.0 se lanzarán en los próximos meses. Para Adobe Commerce local y la versión de Magento Open Source 2.4.0, el Elasticsearch 6.x o 7.x será un componente requerido, y el motor de búsqueda MySQL se eliminará. En Adobe Commerce, en la infraestructura en la nube, ya se requiere Elasticsearch.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# El motor de búsqueda del catálogo MySQL se eliminará en Adobe Commerce 2.4.0

Adobe Commerce local, Adobe Commerce en la infraestructura en la nube y Magento Open Source 2.4.0 se lanzarán en los próximos meses. Para Adobe Commerce local y la versión de Magento Open Source 2.4.0, el Elasticsearch 6.x o 7.x será un componente requerido, y el motor de búsqueda MySQL se eliminará. En Adobe Commerce, en la infraestructura en la nube, ya se requiere Elasticsearch.

>[!WARNING]
>
>Si no se instala/configura el Elasticsearch 6/7 antes de intentar actualizar, podrían producirse problemas graves con Adobe Commerce. Tenga en cuenta que las actualizaciones de servicios en Adobe Commerce en la infraestructura en la nube no se pueden insertar en el entorno de producción sin un aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Así que 48 horas antes de cuando sus cambios deben estar en producción [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detallando la actualización de servicio necesaria e indicando la hora en la que desea que se inicie el proceso de actualización.

La razón para la eliminación del motor de búsqueda MySQL es que Elasticsearch proporciona capacidades de búsqueda superiores, así como optimizaciones de rendimiento del catálogo.

## Productos y versiones afectados:

* Adobe Commerce local v2.4.0
* Magento Open Source v2.4.0

## Actualización:

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>Motor de búsqueda</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>Acción</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">Debe instalar Elasticsearch. Consulte <a href="https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html">Elasticsearch de instalación y configuración</a> en nuestra documentación para desarrolladores.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (sin versión en la lista)</td>
<td style="width: 478.2px;">Utiliza el Elasticsearch 2 y debe actualizar al Elasticsearch 7 (opción preferida) o 6. Consulte <a href="https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html#es-upgrade6">Elasticsearch de actualización</a> y <a href="https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html">Configuración de Commerce para utilizar Elasticsearch</a> en nuestra documentación para desarrolladores para obtener más información.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">El Elasticsearch 5 ha alcanzado su límite <a href="https://www.elastic.co/support/eol">Fin de vida útil</a> y ha quedado obsoleto en Adobe Commerce 2.4.0. Actualice a Elasticsearch 7 (preferido) o 6.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 6 o 7</td>
<td style="width: 478.2px;">No es necesario que realice ningún paso adicional antes de actualizar a Adobe Commerce 2.4.0.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Extensión de terceros</td>
<td style="width: 478.2px;">No es necesario que instale Elasticsearch. Adobe Commerce recomienda ponerse en contacto con el proveedor del motor de búsqueda para determinar si la extensión es totalmente compatible con Adobe Commerce 2.4.0.</td>
</tr>
</tbody>
</table>

## Instalación:

Cuando Adobe Commerce local y Magento Open Source 2.4.0 se publiquen, Elasticsearch será un componente necesario, por lo que debe tener un host de Elasticsearch configurado antes de instalar la versión 2.4.0. Consulte [Elasticsearch de instalación y configuración](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) en nuestra documentación para desarrolladores.

De forma predeterminada, la búsqueda de Adobe Commerce utilizará el Elasticsearch 7 como motor de búsqueda e intentará conectarse a un servidor en localhost:9200. También se admite el Elasticsearch 6.x. Si la configuración no coincide con los valores predeterminados, puede establecerlos con los argumentos pasados a `setup:install`, de la misma manera que se configura la conexión a la base de datos.

Por ejemplo, `setup:install --elasticsearch-host=es.mystore.com`

Durante la instalación, se comprobará la conexión del Elasticsearch y la instalación fallará si Adobe Commerce no puede conectarse a un host del Elasticsearch. Si esto sucede, compruebe que el Elasticsearch esté en funcionamiento y que ha proporcionado los parámetros de conexión correctos.
