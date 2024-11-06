---
title: El panel de navegación superior no se carga en la tienda
description: Este artículo proporciona soluciones de configuración a los problemas de Varnish Edge Side Includes (ESI), donde el contenido de ciertas páginas, generalmente el panel de navegación superior, no se muestra en la tienda si Varnish se usa para el almacenamiento en caché.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# El panel de navegación superior no se carga en la tienda

Este artículo proporciona soluciones de configuración a los problemas de Varnish Edge Side Includes (ESI), donde el contenido de ciertas páginas, generalmente el panel de navegación superior, no se muestra en la tienda si Varnish se usa para el almacenamiento en caché.

## Productos y versiones afectados

* Adobe Commerce 2.X.X
* Todas las versiones de barniz

## Problema

<u>Requisitos previos</u>:

Instale y configure Varnish para su tienda de Adobe Commerce.

<u>Pasos a seguir</u>:

1. Ve a la tienda.
1. Examine las páginas de la tienda.

<u>Resultados esperados</u>:

Todo el contenido y todos los bloques de página se cargan correctamente.

<u>Resultados reales</u>:

Observe que algunos bloques de contenido, como el panel de navegación superior con categorías, no se cargan. Se muestra un espacio en blanco.

## Causa

Los posibles motivos del problema son los siguientes:

* Las etiquetas ESI include se generan con el protocolo de acceso HTTPS, mientras que Varnish solo funciona con HTTP.
* El barniz no procesa ESI dentro de JSON.
* Los encabezados de respuesta son demasiado grandes para Varnish; no puede procesarlos.

## Solución

Para resolver los problemas, debe realizar una configuración adicional de Barnish y reiniciar Varnish.

1. Como usuario con privilegios de `root`, abra el archivo de configuración de Desvanecer en un editor de texto. Consulte [Modificar la configuración del sistema Varnish](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/config-varnish-server) en nuestra documentación para desarrolladores para obtener información sobre dónde se puede ubicar este archivo para diferentes sistemas operativos.
1. En `DAEMON_OPTS variable`, agregue `-p feature=+esi_ignore_https`, `-p  feature=+esi_ignore_other_elements`, `-p  feature=+esi_disable_xml_check`. Este aspecto sería el siguiente:

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. Guarde los cambios y salga del editor de texto.
1. En el archivo de configuración de VCL, aumente los encabezados de respuesta aumentando los valores de estos parámetros: `http_resp_hdr_len`, `http_resp_size`, `workspace_backend`. Asegúrese de que los dos últimos tengan valores similares.
1. Cuando cambie esto, debe ejecutar `service varnish restart` para que los cambios surtan efecto.

## Lectura relacionada

* [Configure Varnish y su servidor web](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/config-varnish-server) en nuestra documentación para desarrolladores.
* [Documentación de barniz](https://varnish-cache.org/docs/5.1/reference/index.html)
