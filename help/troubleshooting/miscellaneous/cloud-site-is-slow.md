---
title: El sitio de la nube es lento
description: Este artículo proporciona recomendaciones sobre cómo mejorar el rendimiento de su sitio de Adobe Commerce en la infraestructura en la nube bajo cargas de tráfico pesadas y cómo reducir esta carga.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# El sitio de la nube es lento

Este artículo proporciona recomendaciones sobre cómo mejorar el rendimiento de su sitio de Adobe Commerce en la infraestructura en la nube bajo cargas de tráfico pesadas y cómo reducir esta carga.

## Versiones y ediciones afectadas

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

<u>Pasos a seguir</u>

1. Visite su tienda de Adobe Commerce.
1. Examine una página de categoría.
1. Añadir un producto al carro de compras.

<u>Resultado esperado</u>

El sitio es adaptable y añadir un producto al carro de compras es rápido.

<u>Resultado real</u>

El sitio es lento o las páginas de categoría son rápidas, pero la página del carro de compras es lenta.

## Pasos y soluciones de depuración

Realice los siguientes pasos para rastrear el motivo del rendimiento lento y solucionarlo. Puede cambiar el primer y el segundo paso, pero continuar bloqueando direcciones IP solo si la optimización de la configuración de la caché no ayuda.

1. Compruebe la tasa de visitas en caché para las páginas con alto tráfico y reduzca la cantidad de datos actualizados.
1. Compruebe la tasa general de visitas de caché del sitio y verifique la configuración general de caché/Fastly.
1. Identifique los clientes web que provocan la carga alta del servidor y bloquee las IP que provocan la carga alta.

Los siguientes párrafos proporcionan más detalles para cada paso.

### Paso 1: Compruebe la tasa de visitas en caché para las páginas con alto tráfico

El primer paso para corregir un sitio atascado por tráfico intenso es garantizar que las páginas con el tráfico más intenso, como la página principal de la tienda y las páginas de categoría de nivel superior, se almacenen en caché correctamente.

Puede averiguar las tasas de aciertos de caché para estas páginas revisando los encabezados HTTP `X-Cache` mediante cURL, tal como se describe en [Comprobación de caché mediante cURL](https://docs.fastly.com/guides/debugging/checking-cache#using-curl) en la documentación de Fastly. O compruebe los mismos encabezados con la pestaña de red de la barra de herramientas del desarrollador de su explorador web favorito.

Fastly suele respetar los encabezados de respuesta procedentes de la aplicación; sin embargo, si todos los encabezados están configurados en &quot;no almacenar en caché&quot; y para que la página &quot;caduque en el pasado&quot;, Fastly no puede almacenar en caché la página.

>[!WARNING]
>
>Tenga en cuenta que cambia rápidamente los encabezados de respuesta, por lo que al comprobar la URL principal con cURL o el explorador web no se muestran necesariamente los encabezados que emite la aplicación. Es común que Fastly responda a exploradores web con encabezados &quot;sin caché&quot;, pero que la propia aplicación web permita el almacenamiento en caché y que Fastly almacene en caché correctamente el elemento. Por lo tanto, la información de los encabezados &quot;cache-control&quot; y &quot;pragma&quot; no será útil en este caso.

#### Solución de problemas para páginas con mucho tráfico

Si la página de índice tiene una tasa de visitas baja, puede corregirla reduciendo la cantidad de datos muy actualizados presentes en esa página.

### Paso 2: Compruebe la tasa global de visitas de caché del sitio

Para comprobar la tasa de aciertos de caché general:

1. [Obtenga credenciales de Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration) para su Adobe Commerce en el entorno de infraestructura en la nube.
1. Ejecute el siguiente comando cURL de Linux/macOS para comprobar la tasa de visitas del sitio durante los últimos 30 minutos, reemplazando y con los valores de las credenciales de Fastly:

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   También puede comprobar las tasas de visitas históricas del último día o mes cambiando la opción de consulta de intervalo de tiempo de `?by=minute` a `?by=hour` o `?by=day`. Para obtener más información sobre cómo obtener estadísticas de caché de Fastly, consulte [Opciones de consulta](https://docs.fastly.com/api/stats#Query) en la documentación de Fastly.

   La opción `| json_pp` imprime correctamente el resultado de la respuesta JSON con la utilidad `json_pp`. Si obtiene un error_&#39;json\_pp not found&#39;_, instale la utilidad `json_pp` o use otra herramienta de línea de comandos para la impresión con sangría de JSON. Como alternativa, elimine el parámetro `| json_pp` y ejecute de nuevo el comando. El resultado de la respuesta JSON no tiene formato, pero puede ejecutarlo a través de un embellecedor JSON para limpiarlo.

Una tasa de visitas superior al 0,90 o al 90 % indica que la caché de página completa está funcionando.

Una tasa de visitas inferior al 0,85 o al 85 % puede indicar un problema de configuración del sitio o puede tener instalada una extensión de terceros que no permite almacenar su contenido en caché.

#### Resolución de problemas de tasa de aciertos de caché general

1. Mediante las estadísticas de tasa de visitas por hora y por día, identifique cuándo comenzó a disminuir la tasa de visitas. Si la tasa de visitas disminuyó repentinamente aproximadamente al mismo tiempo que implementó un cambio en el sitio, considere revertir el cambio hasta que se reduzca la carga del sitio.
1. Compruebe la configuración en el administrador de Commerce, en **Tiendas** > **Configuración** > Avanzada > **Sistema** > **Caché de página completa**. Asegúrese de que el valor **TTL para contenido público** no esté configurado demasiado bajo.
1. Asegúrese de [cargar los fragmentos de VCL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
1. Si utiliza fragmentos de VCL personalizados, devíselos para un uso correcto de las acciones &quot;pass&quot; o &quot;pipe&quot;: deben utilizarse con cuidado y, como mínimo, con una condición de algún tipo. Para obtener más sugerencias, consulte [Fragmentos personalizados de VCL de Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) en nuestra documentación para desarrolladores.

### Paso 3: Identificar los sitios web que causan la alta carga del servidor

Puede utilizar cualquiera de los siguientes métodos para obtener información sobre las direcciones IP que acceden a su tienda Adobe Commerce.

* Compruebe los registros de acceso HTTP a través de una sesión SSH.
* Póngase en contacto con el servicio de asistencia técnica de Adobe Commerce para solicitar una lista de direcciones IP que causen una carga pesada en el sitio.

#### Comprobación de los registros de acceso HTTP

Para ver el registro de acceso del sitio, ejecute el siguiente comando desde el entorno de desarrollo local:

```bash
magento-cloud log access
```

Ver más líneas con

```bash
--lines
```

, por ejemplo:

```bash
magento-cloud log access --lines=500
```

Puede ver este registro y comprobar si una gran parte de las solicitudes provienen de una dirección IP específica. Otra forma es usar `awk`, `sort` y `uniq` para contar automáticamente las direcciones IP que aparecen con más frecuencia en el registro, como las siguientes:

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

Si la variable

```bash
magento-cloud log
```

no funciona, puede conectarse al servidor remoto con SSH y comprobar el archivo de registro en `/var/log/access.log`

Después de identificar las direcciones IP que causan una carga pesada en el servidor, puede bloquearlas configurando una lista de bloqueados IP desde en el panel de administración de Commerce, en **Almacenes** > **Configuración** > AVANZADA > **Sistema** > **Caché de página completa** > **Configuración rápida** > **Bloqueo**.

Si no puede acceder a su administrador debido a una carga pesada, puede utilizar la API de Fastly para configurar las reglas de bloqueo:

1. Cree la ACL como se describe en [Uso de ACL mediante el documento de Fastly de API](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api).
1. En la sección `recv`, cree un fragmento de VCL con el siguiente contenido, después de reemplazar ACL\_NAME\_GOES\_HERE con el nombre de la ACL que se creó en el paso anterior:

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

Para obtener más información sobre cómo bloquear direcciones IP, consulte la [Guía del módulo de Fastly Adobe Commerce](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) en GitHub.
