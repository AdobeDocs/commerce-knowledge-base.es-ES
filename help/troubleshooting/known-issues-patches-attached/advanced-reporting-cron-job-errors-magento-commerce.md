---
title: Adobe Commerce de errores cron de trabajo de informes avanzados
description: Este artículo proporciona parches para los problemas de trabajos cron de informes avanzados en Adobe Commerce, que pueden provocar un error 404 en los clientes que intentan acceder a los informes avanzados.
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce de errores cron de trabajo de informes avanzados

Este artículo proporciona parches para los problemas de trabajos cron de informes avanzados en Adobe Commerce, que pueden provocar un error 404 en los clientes que intentan acceder a los informes avanzados.

## Productos y versiones afectados

Adobe Commerce (todas las opciones de implementación) 2.3.x

## Problema

Un cliente recibe un error 404 cuando intenta acceder a la creación de informes avanzada y hay errores en los registros asociados a `analytics_collect_data job` .

## Versiones de Magento compatibles:

Los parches son compatibles (pero es posible que no resuelvan el problema) con las siguientes versiones y ediciones de Adobe Commerce:

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip): Adobe Commerce (todas las opciones de implementación) 2.3.1-2.3.4-p2
* [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (todas las opciones de implementación) 2.3.0
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (todas las opciones de implementación) 2.3.0

## **Solución**

Para solucionar el problema, aplique el parche correspondiente adjunto a este artículo. Para descargarlo, haga clic en los siguientes vínculos:

* Descargar [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)
* Descargar [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* Descargar [MDVA-18980\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

Para comprobar qué parche utilizar:

<ol><li>Revise los registros mediante el siguiente comando:<code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>Según el error que vea, seleccione un parche con la información de la tabla siguiente.<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>Error</p>
</td>
<td class="wysiwyg-text-align-center">Parche</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL: Error al ejecutar un trabajo cron {"exception":"[object] (RuntimeException(code: 0): Error al ejecutar un trabajo cron en /srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php:327, TypeError(code: 0): substr_count() espera que el parámetro 1 sea una cadena, nulo se da en /srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php:106)"} []</pre>O<pre>report.ERROR: el trabajo cron analytics_collect_data tiene un error: substr_count() espera que el parámetro 1 sea una cadena, dado un valor nulo. Estadísticas: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384}
  [] []</pre>
<p> </p>
</td>
<td>Aplicar<a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch">MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip</a>, borre la caché y espere 24 horas para que el trabajo se ejecute de nuevo e inténtelo de nuevo.</td>
</tr>
<tr>
<td>
<p><em>Error al abrir el archivo /tmp/analytics/tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/.../tmp/../tmp/../tmp/.../</em></p>
</td>
<td>Aplicar<a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch">MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip</a>, borre la caché y espere 24 horas para que el trabajo se ejecute de nuevo e inténtelo de nuevo.</td>
</tr>
<tr>
<td><em>Cifrado no válido</em></td>
<td>Aplicar<a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch">MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip</a>, borre la caché y espere 24 horas para que el trabajo se ejecute de nuevo e inténtelo de nuevo.</td>
</tr>
</tbody>
</table>
</li></ol>

## Cómo aplicar el parche

Descomprima el archivo y siga las instrucciones en [Cómo aplicar un parche del compositor proporcionado por el Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Lectura relacionada

[El archivo no se puede eliminar. Advertencia: no existe el error de archivo o directorio del administrador.](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
