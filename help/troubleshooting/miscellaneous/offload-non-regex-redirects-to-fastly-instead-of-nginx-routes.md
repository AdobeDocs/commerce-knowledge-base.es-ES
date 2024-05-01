---
title: Descargar redirecciones no regex a Fastly en lugar de Nginx (rutas)
description: En este tema se sugiere una solución a un problema típico de rendimiento de redirecciones que podría tener al descargar redirecciones no regex a Fastly en lugar de Nginx en Adobe Commerce en la infraestructura en la nube.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Descargar redirecciones no regex a Fastly en lugar de Nginx (rutas)

En este tema se sugiere una solución a un problema típico de rendimiento de redirecciones que podría tener al descargar redirecciones no regex a Fastly en lugar de Nginx en Adobe Commerce en la infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube (todas las versiones) `Master/Production/Staging` Entornos que se aprovechan rápidamente

## Problema

En Adobe Commerce, en la infraestructura de la nube, no se pueden realizar grandes cantidades de redirecciones/reescrituras que no sean de regex en la capa Nginx y, como resultado, pueden causar problemas de rendimiento.

## Causa

El `routes.yaml` archivo en el `.magento/routes.yaml` define las rutas para su Adobe Commerce en la infraestructura en la nube.

Si el tamaño de su `routes.yaml` tiene 32 KB o más, debería descargar las redirecciones/reescrituras que no sean de regex a Fastly.

Esta capa de Nginx no puede gestionar un gran número de redirecciones/reescrituras que no sean de regex, o se producirán problemas de rendimiento.

## Solución

La solución es descargar esas redirecciones no regex a Fastly en su lugar. Cree una ruta de error genérica para redirigir a Fastly.

Los siguientes pasos detallarán cómo colocar redirecciones en Fastly en lugar de Nginx.

1. Crear un diccionario de Edge.

   En primer lugar, puede utilizar [Fragmentos de VCL en Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) para definir un diccionario de Edge. Esto contendrá las redirecciones.

   Algunas advertencias a esto:

   * Fastly no puede hacer regex en las entradas de diccionario. Es sólo una coincidencia exacta. Para obtener más información sobre estas limitaciones, consulte [Documentos de Fastly sobre las limitaciones de los diccionarios de Edge](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * Fastly tiene un límite de 1000 entradas en un solo diccionario. Puede ampliar rápidamente este límite, pero eso conduce a la tercera advertencia.
   * Cada vez que actualiza las entradas e implementa ese VCL actualizado en todos los nodos, hay un aumento geométrico del tiempo de carga con diccionarios en expansión; es decir, un diccionario de 2000 entradas en realidad se cargará de 3 a 4 veces más lento que un diccionario de 1000 entradas. Pero eso es solo un problema cuando se implementa el VCL (actualizar el diccionario o cambiar el código de función VCL).

     No afecta al tiempo que se tarda rápidamente en procesar una solicitud; solo afecta al tiempo que tarda Fastly en expulsar una nueva configuración.

     En términos generales, los cambios de configuración tardan unos segundos de media, no suelen superar los 5-10 segundos. Por lo tanto, un aumento del doble en los elementos de diccionario tarda más de 30 segundos en implementar la configuración. Un aumento de 4 veces tomaría cerca de 2 minutos. Esto nos lleva a la cuarta advertencia.

   * Hay un límite bastante estricto de 10 000 entradas en un diccionario de Edge.

   Se recomienda consolidar en la lista de redirecciones. Puede utilizar varios diccionarios, pero tenga en cuenta que cualquier actualización que realice en su VCL tardará varios minutos en propagarse por Fastly.

1. Compare la URL con los diccionarios.

   Cuando se produce la búsqueda de URL, se realiza la comparación para aplicar el código de error personalizado si se encuentra una coincidencia.

   Utilice otro fragmento de VCL para agregar algo similar a lo siguiente a `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Aquí, estamos comprobando si la URL existe en la entrada de la tabla. Si es así, se llama a un error interno de Fastly y se pasa a ese error la dirección URL de redireccionamiento de la tabla.

1. Administrar el redireccionamiento.

   Cuando se encuentra una coincidencia, se realiza la acción que está definida para eso `obj.status`, en este caso un redireccionamiento de movimiento permanente 301.

   Uso de un fragmento final en `vcl_error` para devolver los códigos de error 301 al cliente:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Con este bloque, estamos comprobando si el código de error pasado desde `vcl_recv` coincide y, si es así, estableceremos la ubicación en el mensaje de error transmitido y, a continuación, cambiaremos el código de estado a 301 y el mensaje a &quot;Movido permanentemente&quot;. En ese momento, la respuesta debe estar lista para volver al cliente.

### Servicio de fase

>[!WARNING]
>
>Si desea probar todos estos pasos, se recomienda configurar un entorno de ensayo de Adobe Commerce. De este modo, puede ejecutar pruebas en el servicio Fastly para asegurarse de que todo se comporta como cabría esperar.

Si no desea ejecutar un entorno de ensayo de Adobe Commerce, pero desea ver el aspecto que tendrían estas redirecciones, puede configurar una cuenta de ensayo directamente en Fastly.

## Lectura relacionada

* [Referencia de VCL de Fastly](https://docs.fastly.com/vcl/)
* [Configuración de rutas](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) en nuestra documentación para desarrolladores.
* [Configuración rápida](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) en nuestra documentación para desarrolladores.
* [Hoja de trucos de expresiones regulares VCL](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) en nuestra documentación para desarrolladores.
