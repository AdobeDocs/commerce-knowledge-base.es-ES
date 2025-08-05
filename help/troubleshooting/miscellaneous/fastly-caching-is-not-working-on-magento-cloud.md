---
title: El almacenamiento en caché rápido no funciona en Adobe Commerce en la infraestructura en la nube
description: Este artículo proporciona una corrección para el almacenamiento en caché de Fastly, que no funciona en el sitio. Fastly es un servicio de CDN y almacenamiento en caché incluido con Adobe Commerce en planes e implementaciones de infraestructura en la nube. Para verificar que la extensión de Fastly funciona o para depurar la extensión de Fastly, puede utilizar el comando curl para mostrar ciertos encabezados de respuesta. Los valores de estos encabezados de respuesta indican si Fastly está habilitado y funciona correctamente. Puede investigar más a fondo los problemas en función de los valores de los encabezados y del comportamiento del almacenamiento en caché.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# El almacenamiento en caché rápido no funciona en Adobe Commerce en la infraestructura en la nube

Este artículo proporciona una corrección para el almacenamiento en caché de Fastly, que no funciona en el sitio. Fastly es un servicio de CDN y almacenamiento en caché incluido con Adobe Commerce en planes e implementaciones de infraestructura en la nube. Para verificar que la extensión de Fastly funciona o para depurar la extensión de Fastly, puede utilizar el comando curl para mostrar ciertos encabezados de respuesta. Los valores de estos encabezados de respuesta indican si Fastly está habilitado y funciona correctamente. Puede investigar más a fondo los problemas en función de los valores de los encabezados y del comportamiento del almacenamiento en caché.

Esta información le ayuda a verificar y probar los encabezados de Fastly para su sitio activo y servidores de origen.

## Versiones afectadas

* Adobe Commerce en la infraestructura en la nube
* Fastly 1.2.27 y posterior

## Problema

Es posible que el almacenamiento en caché no funcione para los entornos del sitio activo, de producción o de ensayo.

## Causa

Normalmente, las configuraciones, las credenciales incorrectas o las extensiones de Adobe Commerce no admitidas son el problema de que el almacenamiento en caché de Fastly no funciona. Si configura Fastly de forma incorrecta o utiliza una extensión no compatible que elimina los encabezados, el almacenamiento en caché de Fastly no funcionará.

## Probar con comandos y comprobar encabezados de respuesta

### Probar con el comando dig

En primer lugar, compruebe los encabezados con un comando dig en la dirección URL. En una aplicación de terminal, escriba dig `<url>` para comprobar que los servicios de Fastly se muestran en los encabezados. Para obtener más pruebas de excavación, consulte [Prueba de Fastly antes de cambiar el DNS](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains).

Por ejemplo:

* Sitio activo: `dig http[s]://<your domain>`
* Ensayo: `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* Producción: `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### Probar con el comando curl

A continuación, utilice un comando curl para comprobar que existen X-Magento-Tags e información de encabezado adicional. El formato del comando difiere para Ensayo y Producción.

Para obtener más información acerca de estos comandos, omita Fastly al insertar `-H "host:URL"`, reemplace con origin en la ubicación de conexión (información CNAME de la hoja de cálculo de OneDrive), `-k` ignora SSL y `-v` proporciona respuestas detalladas. Si los encabezados se muestran correctamente, compruebe el sitio activo y vuelva a comprobar los encabezados.

* Si se producen problemas de encabezado al visitar directamente los servidores de origen omitiendo Fastly, es posible que tenga problemas en el código, con extensiones o con la infraestructura.
* Si no encuentra errores que afecten directamente a los servidores de origen, pero faltan encabezados que afecten al dominio activo mediante Fastly, puede tener errores de Fastly.

En primer lugar, compruebe su **sitio activo** para comprobar los encabezados de respuesta. El comando pasa por la extensión Fastly para recibir respuestas. Si no recibe los encabezados correctos, debe probar los servidores de origen directamente. Este comando devuelve los valores de los encabezados `Fastly-Magento-VCL-Uploaded` y `X-Cache`.

1. En un terminal, introduzca el siguiente comando para probar la dirección URL activa del sitio:

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   Use `--resolve` solo si la dirección URL activa no está configurada con DNS y no tiene establecida una ruta estática. Por ejemplo:

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. Compruebe los encabezados de respuesta para asegurarse de que Facebook funciona. La salida de este comando es similar a curl Staging y Production. Por ejemplo, debería ver los encabezados únicos devueltos por este comando:

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

Para probar **Staging**:

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Para probar **Equilibrador de carga de producción**:

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Para probar **nodo de origen de producción**:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Un nodo Origin directo:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Por ejemplo, si tiene una dirección URL pública www.mymagento.biz, introduzca un comando similar al siguiente para probar el sitio de producción:

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### Comprobar encabezados de respuesta

* Compruebe los encabezados y valores de respuesta devueltos:
* Fastly-Magento-VCL-Uploaded debe estar presente
* X-Magento-Tags debería devolverse
* Fastly-Module-Enabled debe ser Sí o el número de versión de la extensión Fastly
* X-Cache debe ser HIT o HIT, HIT
* x-cache-hits debería ser 1,1
* Cache-Control: max-age debe ser mayor que 0
* Pragma debe almacenarse en caché

El siguiente ejemplo muestra los valores correctos para Pragma, X-Magento-Tags y Fastly-Module-Enabled.

La salida de los comandos curl puede ser larga. El siguiente es solo un resumen:

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## Resolver

### Fastly-Module-Enabled no está presente

Si no recibe un &quot;sí&quot; para Fastly-Module-Enabled en los encabezados de respuesta, debe verificar que el módulo Fasty esté instalado y seleccionado.

Para comprobar que Fastly está habilitado en ensayo y producción, compruebe la configuración en el administrador de Commerce para cada entorno:

1. Inicie sesión en Admin Console para ensayo y producción utilizando la URL con /admin (o la URL de administración modificada).
1. Vaya a Tiendas > Configuración > Avanzadas > Sistema. Desplácese y haga clic en Caché de página completa.
1. Asegúrese de que ha seleccionado Fastly CDN.
1. Haga clic en Configuración rápida. Asegúrese de introducir el ID del servicio de Fastly y el token de la API de Fastly (sus credenciales de Fastly). Compruebe que ha introducido las credenciales correctas para el entorno de ensayo y producción. Haga clic en Probar credenciales para ayudarle.
1. Edite su composer.json y asegúrese de que el módulo Fasty se incluye con la versión. Este archivo tiene todos los módulos enumerados con versiones.

   * En la sección &quot;requerir&quot;, debería tener &quot;fastly/magento2&quot;: `<version number>`
   * En la sección &quot;repositorios&quot; debería tener:

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. Si utiliza la administración de configuración, debería tener un archivo de configuración. Edite el archivo app/etc/config.app.php (2.0, 2.1) o app/etc/config.php (2.2) y asegúrese de que la configuración `'Fastly_Cdn' => 1` sea correcta. La configuración no debe ser `'Fastly_Cdn' => 0` (lo que significa deshabilitado). Si habilitó Fastly, elimine el archivo de configuración y ejecute el comando bin/magento magento-cloud:scd-dump para actualizar. Para ver una descripción detallada de este archivo, consulte [Ejemplo de administración de la configuración específica del sistema](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=es#manage-the-system-specific-configuration) en la Guía de configuración.

Si el módulo no está instalado, debe instalarlo en una rama de [entorno de integración](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-27242) e implementarlo en Ensayo y producción. Consulte [Configuración rápida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=es) para obtener instrucciones en la Guía de Commerce sobre infraestructura en la nube.

### Fastly-Magento-VCL-Uploaded no está presente

Durante la instalación y configuración, debería haber cargado Fastly VCL. Estos son los fragmentos de VCL básicos que proporciona el módulo Fastly, no los fragmentos de VCL personalizados que crea. Para obtener instrucciones, consulte [Cargar fragmentos de VCL de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=es#upload-vcl-to-fastly) en la Guía de infraestructura de Commerce en la nube.

### X-Cache incluye MISS

Si X-Cache es HIT, MISS o MISS, MISS, introduzca de nuevo el mismo comando de flexión para asegurarse de que la página no se haya expulsado recientemente de la caché.

Si obtiene el mismo resultado, utilice los comandos curl y compruebe los encabezados de respuesta:

* El Pragma es caché
* X-Magento-Tags existe
* Cache-Control: max-age es mayor que 0

Si el problema persiste, es probable que otra extensión restablezca estos encabezados. Repita el siguiente procedimiento en Ensayo para desactivar las extensiones y encontrar cuál es la causa del problema. Después de localizar las extensiones que causan el problema, deberá deshabilitar las extensiones en Producción.

1. Para deshabilitar las extensiones, siga los pasos que se indican en la sección [Administrar extensiones](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=es#manage-extensions) de la guía de Commerce en infraestructura de nube.
1. Después de deshabilitar las extensiones, vaya a **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**.
1. Haga clic en **[!UICONTROL Flush Magento Cache]**.
1. Ahora habilite una extensión a la vez, guardando la configuración y vaciando la caché.
1. Pruebe los comandos curl y compruebe los encabezados de respuesta.
1. Repita los pasos 4 y 5 para activar y probar los comandos curl. Cuando los encabezados de Fastly ya no se muestran, ha encontrado la extensión que causa problemas con Fastly.

Cuando aísle la extensión que está restableciendo los encabezados de Fastly, póngase en contacto con el desarrollador de la extensión para obtener ayuda adicional. No podemos proporcionar correcciones o actualizaciones para que los desarrolladores de extensiones de terceros trabajen con el almacenamiento en caché de Fastly.

## Más información en nuestra documentación para desarrolladores:

* [Acerca de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=es)
* [Configurar rápidamente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=es)
* [Fragmentos personalizados de VCL de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=es)
