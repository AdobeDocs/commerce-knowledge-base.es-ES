---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# Guía de etiquetas de KB

Este documento proporciona directrices para agregar etiquetas a artículos en la Base de conocimiento de soporte de Adobe Commerce.
Las etiquetas (también denominadas etiquetas) mejoran la experiencia de búsqueda en [Adobe Commerce Support Knowledge Base](https://support.magento.com/hc/en-us).
Las etiquetas se añaden en el campo &quot;etiquetas&quot; de la sección de metadatos de un archivo de artículo, separadas por comas, sin espacio entre una coma y la siguiente etiqueta.
Consulte [../../.github/CONTRIBUTING.md#metadata] para obtener más información.

## Disposiciones generales

Para cada artículo, agregue los siguientes tipos de etiquetas:

* Etiqueta(s) para producto(s). (obligatorio)
* Etiqueta(s) para las versiones afectadas. (obligatorio, excepto artículos relacionados con el soporte general)
* Etiqueta para el tipo de contenido. (obligatorio)
* Etiquetas para los principales componentes tecnológicos.(si procede)
* Etiquetas para el proceso/funcionalidad que se está solucionando/describiendo. (si procede)
* Etiquetas del problema que se está solucionando/describiendo. (si procede)

Consulte las secciones siguientes para obtener recomendaciones detalladas sobre cómo definir etiquetas para cada uno de estos tipos de etiquetas.

## Etiquetas para productos

<table>
<tbody>
  <tr>
    <th>Nombre del producto</th>
    <th>Etiqueta</th>
  </tr>
  <tr>
    <td>Adobe Commerce (todos los métodos de implementación) </td>
    <td>
    "Adobe Commerce, infraestructura en la nube, local"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce en la infraestructura en la nube</td>
    <td>
      "Adobe Commerce, infraestructura en la nube"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce local</td>
    <td>"Adobe Commerce, local"</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence (MBI)</td>
    <td>
        "Magento Business Intelligence, MBI"
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>B2B para Adobe Commerce</td>
    <td>B2B</td>
  </tr>
  <tr>
    <td>PWA para Adobe Commerce</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Proyecto de Tienda Venia</td>
    <td>"Venia"</td>
  </tr>
  <tr>
    <td>Herramienta Parches de calidad, QPT</td>
    <td>"Herramienta Parches de calidad,Parches QPT"</td>
  </tr>
  </tbody>
</table>

## Etiquetas para versiones de productos

* Agregue una etiqueta independiente para cada versión de Adobe Commerce. Ejemplo: &quot;2.3.7&quot;
* No agregue etiquetas para los intervalos.
Es decir, si 2.3.0-2.3.5 se ve afectado, añada: &quot;2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2&quot;
NO &quot;2.3.0-2.3.5&quot;
* No agregue etiquetas con .x. Ejemplo: &quot;2.3.x&quot;

## Etiquetas para el tipo de contenido (según la categoría)

<table>
  <tbody>
    <tr>
      <th>Categoría</th>
      <th>Etiqueta</th>
    </tr>
    <tr>
      <td>Prácticas recomendadas</td>
      <td>"prácticas recomendadas" (no "prácticas recomendadas" ni "prácticas recomendadas")</td>
    </tr>
    <tr>
      <td>
        Resolución de problemas
      </td>
      <td>
      "resolución de problemas"
      </td>
    </tr>
    <tr>
      <td>Cómo:</td>
      <td>"cómo"</td>
    </tr>
    <tr>
      <td>FAQ</td>
      <td >"FAQ"</td>
    </tr>
  </tbody>
</table>

## Etiquetas para componentes técnicos principales

* Utilice mayúsculas según la denominación oficial del componente.
* No utilice sinónimos, una etiqueta para un componente.
* Es preferible utilizar una etiqueta de palabra, pero si el nombre del componente contiene varias palabras, utilice varias palabras. No agregue descripciones de problemas. Es decir, ponga &quot;Elasticsearch&quot; en lugar de &quot;problemas de Elasticsearch&quot;.
* Si el contenido solo es relevante para una versión concreta del componente, añada una etiqueta que contenga nombre + versión.\
  Ejemplo: &quot;Elasticsearch 5&quot;. Si es relevante para varias versiones en particular, añada varias etiquetas de este tipo. Ejemplo: &quot;Elasticsearch 5&quot;, &quot;Elasticsearch 6&quot;. Si es relevante, utilice &quot;x&quot; para varias versiones. Ejemplo: &quot;Elasticsearch 2.x&quot;

Ejemplos:

* &quot;Elasticsearch&quot;
* &quot;New Relic&quot;
* &quot;Asistente para configuración web&quot;

## Etiquetas para el proceso/funcionalidad que se está solucionando/describiendo

* Utilice minúsculas, excepto los sustantivos propios.
* No utilice sinónimos, una etiqueta para una entidad.
* Es preferible utilizar etiquetas de una sola palabra. No añadir descripción de problema. Es decir, ponga &quot;base de datos&quot; en lugar de &quot;bloqueos de base de datos&quot;.

Ejemplos: 

* &quot;base de datos&quot;
* &quot;cron&quot;
* &quot;implementación&quot;
* &quot;actualización masiva&quot;

## Etiquetas del problema que se está solucionando/describiendo

* Utilice minúsculas, con la excepción de los sustantivos propios.
* No utilice sinónimos, una etiqueta para una entidad.
* Es preferible utilizar etiquetas de una sola palabra. No convierta un mensaje de error en una etiqueta.

Ejemplos:

* &quot;sitio caído&quot;
* &quot;Error 500&quot;
* &quot;cron atascado&quot;
