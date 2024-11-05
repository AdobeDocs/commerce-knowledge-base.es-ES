---
title: 'Descargar redirecciones que no sean de [!DNL regex] a [!DNL Fastly] en lugar de [!DNL Nginx] (rutas)'
description: Este tema sugiere una solución a un problema típico de rendimiento de redirecciones que podría tener cuando descargue redirecciones que no sean de [!DNL regex] a  [!DNL Fastly] en lugar de [!DNL Nginx] en Adobe Commerce en la infraestructura en la nube.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Descargar redirecciones que no sean de [!DNL regex] a [!DNL Fastly] en lugar de [!DNL Nginx] (rutas)

En este tema se sugiere una solución a un problema típico de rendimiento de redirecciones que podría tener al descargar redirecciones que no son de [!DNL regex] a [!DNL Fastly] en lugar de [!DNL Nginx] en Adobe Commerce en la infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la nube (todas las versiones) `Master/Production/Staging` entornos que aprovechan [!DNL Fastly]

## Problema

En Adobe Commerce en la infraestructura de la nube, no se pueden realizar grandes cantidades de redirecciones/reescrituras que no sean de [!DNL regex] en la capa [!DNL Nginx] y, como resultado, pueden causar problemas de rendimiento.

## Causa

El archivo `routes.yaml` del directorio `.magento/routes.yaml` define las rutas para su Adobe Commerce en la infraestructura de la nube.

Si el tamaño del archivo de `routes.yaml` es de 32 KB o más, debería descargar las redirecciones y reescrituras que no sean de [!DNL regex] en [!DNL Fastly].

Esta capa [!DNL Nginx] no puede administrar un gran número de redirecciones/reescrituras que no sean [!DNL regex], de lo contrario se producirán problemas de rendimiento.

## Solución

La solución consiste en descargar esas redirecciones que no sean de [!DNL regex] a [!DNL Fastly]. Cree una ruta de error genérica para redirigir a [!DNL Fastly].

Los siguientes pasos detallarán cómo colocar redirecciones en [!DNL Fastly] en lugar de [!DNL Nginx].

1. Crear un diccionario de Edge.

   Primero, puede usar [[!DNL VCL] fragmentos de código en Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) para definir un diccionario de Edge. Esto contendrá las redirecciones.

   Algunas advertencias a esto:

   * [!DNL Fastly] no puede [!DNL regex] en las entradas de diccionario. Es sólo una coincidencia exacta. Para obtener más información sobre estas limitaciones, consulte los documentos de [[!DNL Fastly] sobre las limitaciones de los diccionarios de Edge](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * [!DNL Fastly] tiene un límite de 1000 entradas en un solo diccionario. [!DNL Fastly] puede ampliar este límite, pero eso lleva a la tercera advertencia.
   * Cada vez que actualiza las entradas e implementa ese(a) [!DNL VCL] actualizado(a) en todos los nodos, hay un aumento geométrico del tiempo de carga con diccionarios ampliados; es decir, un diccionario de 2000 entradas cargará de 3x-4x más lento que un diccionario de 1000 entradas. Pero eso es solo un problema cuando está implementando [!DNL VCL] (actualizando el diccionario o cambiando el código de función [!DNL VCL]).

     No influye en el tiempo que tarda [!DNL Fastly] en procesar una solicitud; solo influye en el tiempo que tarda [!DNL Fastly] en expulsar una nueva configuración.

     En términos generales, los cambios de configuración tardan unos segundos de media, no suelen superar los 5-10 segundos. Por lo tanto, un aumento del doble en los elementos de diccionario tarda más de 30 segundos en implementar la configuración. Un aumento de 4 veces tomaría cerca de 2 minutos. Esto nos lleva a la cuarta advertencia.

   * Hay un límite bastante estricto de 10 000 entradas en un diccionario de Edge.

   Se recomienda consolidar en la lista de redirecciones. Puede usar varios diccionarios, pero tenga en cuenta que cualquier actualización que haga en su [!DNL VCL] tardará varios minutos en propagarse a lo largo de [!DNL Fastly].

1. Comparar [!DNL URL] con los diccionarios.

   Cuando se realice la búsqueda [!DNL URL], se realizará la comparación para aplicar el código de error personalizado si se encuentra una coincidencia.

   Use otro fragmento de código [!DNL VCL] para agregar algo similar a lo siguiente a `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Aquí estamos comprobando si [!DNL URL] existe en la entrada de tabla. Si es así, llamaremos a un error [!DNL Fastly] interno y pasaremos a ese error el redireccionamiento [!DNL URL] desde la tabla.

1. Administrar el redireccionamiento.

   Cuando se encuentra una coincidencia, se realiza la acción definida para ese(a) `obj.status`, en este caso una redirección de movimiento permanente 301.

   Use un último fragmento de código en `vcl_error` para devolver los códigos de error 301 al cliente:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Con este bloque, estamos comprobando si el código de error pasado desde `vcl_recv` coincide y, si es así, estableceremos la ubicación en el mensaje de error pasado, luego cambiaremos el código de estado a 301 y el mensaje a &quot;Movido permanentemente&quot;. En ese momento, la respuesta debe estar lista para volver al cliente.

### Servicio de fase

>[!WARNING]
>
>Si desea probar todos estos pasos, se recomienda configurar un entorno de ensayo de Adobe Commerce. De este modo, puede ejecutar pruebas en el servicio [!DNL Fastly] para asegurarse de que todo se comporta como cabría esperar.

Si no desea ejecutar un entorno de ensayo de Adobe Commerce, pero desea ver el aspecto que tendrían estas redirecciones, puede configurar una cuenta de ensayo directamente en [!DNL Fastly].

## Lectura relacionada

* [[!DNL Fastly VCL] referencia](https://docs.fastly.com/vcl/)
* [Configurar rutas](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) en nuestra documentación para desarrolladores
* [Configurado [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) en nuestra documentación para desarrolladores
* [[!DNL VCL] hoja de referencia de expresiones regulares](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) en nuestra documentación para desarrolladores
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
