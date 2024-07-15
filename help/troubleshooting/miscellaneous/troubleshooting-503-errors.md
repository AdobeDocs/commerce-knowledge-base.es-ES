---
title: Solución de problemas de error 503 causado por la necesidad de cambiar la configuración predeterminada de Barniz
description: Este artículo proporciona soluciones para la resolución de errores 503 causados por ciertos valores predeterminados de caché de barniz que no son suficientes para su tienda.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 9c5e993b69a98865a1142110625252da848eae04
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Solución de problemas de error 503 causado por la necesidad de cambiar la configuración predeterminada de Barniz

Este artículo proporciona soluciones para la resolución de errores 503 causados por ciertos valores predeterminados de caché de barniz que no son suficientes para su tienda.

## Problema

Si la longitud de las etiquetas de caché utilizadas por Adobe Commerce supera el valor predeterminado de Varnish de 8192 bytes, puede ver errores HTTP 503 (Error de recuperación de back-end) en el explorador. Los errores pueden mostrarse de forma similar a los siguientes: *&quot;Error 503 Error al recuperar el servidor. Error al obtener back-end&quot;*

## Solución

Para resolver este problema, aumente el valor predeterminado del parámetro `http_resp_hdr_len` en el archivo de configuración de Barniz. El parámetro `http_resp_hdr_len` especifica la longitud máxima del encabezado *en* el tamaño total de respuesta predeterminado de 32768 bytes.

>[!NOTE]
>
>Si el valor `http_resp_hdr_len` supera los 32 K, también debe aumentar el tamaño de respuesta predeterminado con el parámetro `http_resp_size`.

1. Como usuario con privilegios de `root`, abra el archivo de configuración de Desvanecer en un editor de texto:
   * CentOS 6: `/etc/sysconfig/varnish`
   * CentOS 7: `/etc/varnish/varnish.params`
   * Debian: `/etc/default/varnish`
   * Ubuntu: `/etc/default/varnish`
1. Busque el parámetro `http_resp_hdr_len`.
1. Si el parámetro no existe, agréguelo después de `thread_pool_max`
1. Establezca `http_resp_hdr_len` en un valor igual al recuento de productos de la categoría más grande multiplicado por 21. (Cada etiqueta de producto tiene una longitud de aproximadamente 21 caracteres).    Por ejemplo, configurar el valor en 65536 bytes debería funcionar si la categoría más grande tiene 3000 productos.    Por ejemplo:    ```conf    -p http_resp_hdr_len=65536 \    ```
1. Establezca `http_resp_size` en un valor que se ajuste a la longitud de encabezado de respuesta incrementada.    Por ejemplo, el uso de la suma de la longitud del encabezado aumentada y el tamaño de respuesta predeterminado es un buen punto de partida (por ejemplo, 65536 + 32768 = 98304): `-p http_resp_size=98304`. A continuación se muestra un fragmento:

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## Tiempos de espera de comprobación de estado {#health-check-timeouts}

Si desactiva la caché mientras Varnish está configurado como aplicación de almacenamiento en caché y mientras Adobe Commerce está en modo de desarrollador, puede que sea imposible iniciar sesión en Admin.

Esta situación podría suceder porque la comprobación de estado predeterminada tiene un valor de `timeout` de 2 segundos. La comprobación de estado puede tardar más de dos segundos en recopilar y combinar la información de cada solicitud de comprobación de estado. Si esto sucede en 6 de cada 10 comprobaciones de estado, el servidor de Adobe Commerce se considera no saludable. El barniz proporciona contenido obsoleto cuando el servidor no está en buen estado.

Dado que se accede al administrador a través de Varnish, no puede iniciar sesión en Admin para habilitar el almacenamiento en caché (a menos que Adobe Commerce vuelva a estar en buen estado). Sin embargo, puede utilizar el siguiente comando para habilitar la caché:

```bash
$ bin/magento cache:enable
```

Para obtener más información acerca del uso de la línea de comandos, vea [Introducción a la configuración de la línea de comandos](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands.html).
