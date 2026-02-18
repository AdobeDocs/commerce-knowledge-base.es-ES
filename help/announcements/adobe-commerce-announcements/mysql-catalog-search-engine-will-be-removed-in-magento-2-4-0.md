---
title: El motor de búsqueda del catálogo MySQL se eliminará en Adobe Commerce 2.4.0
description: Adobe Commerce local, Adobe Commerce en la infraestructura en la nube y Magento Open Source 2.4.0 se lanzarán en los próximos meses. Para Adobe Commerce local y Magento Open Source versión 2.4.0 Elasticsearch 6.x o 7.x será un componente requerido, y el motor de búsqueda MySQL se eliminará. En Adobe Commerce, en la infraestructura en la nube, Elasticsearch ya es obligatorio.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# El motor de búsqueda del catálogo MySQL se eliminará en Adobe Commerce 2.4.0

Adobe Commerce local, Adobe Commerce en la infraestructura en la nube y Magento Open Source 2.4.0 se lanzarán en los próximos meses. Para Adobe Commerce local y Magento Open Source versión 2.4.0 Elasticsearch 6.x o 7.x será un componente requerido, y el motor de búsqueda MySQL se eliminará. En Adobe Commerce, en la infraestructura en la nube, Elasticsearch ya es obligatorio.

>[!WARNING]
>
>Si no se instala/configura Elasticsearch 6/7 antes de intentar actualizar, podrían producirse problemas graves con Adobe Commerce. Tenga en cuenta que las actualizaciones de servicios en Adobe Commerce en la infraestructura en la nube no se pueden insertar en el entorno de producción sin un aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Así que 48 horas antes de que sus cambios deban estar en producción [envíe un ticket de soporte](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) detallando su actualización de servicio requerida e indicando la hora en que desea que comience el proceso de actualización.

El motivo para eliminar el motor de búsqueda MySQL es que Elasticsearch proporciona funcionalidades de búsqueda superiores, así como optimizaciones de rendimiento del catálogo.

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
<td style="width: 478.2px;">Debe instalar Elasticsearch. Consulte <a href="https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/search/overview-search">Instalar y configurar Elasticsearch</a> en nuestra documentación para desarrolladores.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (sin versión en la lista)</td>
<td style="width: 478.2px;">Utiliza Elasticsearch 2 y debe actualizar a Elasticsearch 7 (opción preferida) o 6. Consulte <a href="https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">Actualización de Elasticsearch</a> y <a href="https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/search/configure-search-engine">Configuración de Commerce para usar Elasticsearch</a> en nuestra documentación para desarrolladores para obtener más información.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">Elasticsearch 5 ha llegado a su <a href="https://www.elastic.co/support/eol">fin de vida útil</a> y ha quedado obsoleto en Adobe Commerce 2.4.0. Actualice a Elasticsearch 7 (preferido) o 6.</td>
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

Cuando Adobe Commerce local y Magento Open Source 2.4.0 se publiquen, Elasticsearch serán un componente necesario, por lo que debe tener un host de Elasticsearch configurado antes de instalar la versión 2.4.0. Consulte [Instalar y configurar Elasticsearch](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/search/overview-search) en nuestra documentación para desarrolladores.

De manera predeterminada, la búsqueda de Adobe Commerce usará Elasticsearch 7 como motor de búsqueda e intentará conectarse a un servidor en localhost:9200. Elasticsearch 6.x también es compatible. Si la configuración no coincide con los valores predeterminados, puede configurarlos con los argumentos pasados a `setup:install`, de la misma manera que se configura la conexión a la base de datos.

Por ejemplo, `setup:install --elasticsearch-host=es.mystore.com`

Durante la instalación, se comprobará la conexión de Elasticsearch y la instalación fallará si Adobe Commerce no puede conectarse a un host de Elasticsearch. Si esto sucede, compruebe que Elasticsearch esté operativo y que haya proporcionado los parámetros de conexión correctos.
