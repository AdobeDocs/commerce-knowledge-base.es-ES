---
title: Cuello de botella de carga alta MySQL en Adobe Commerce en la infraestructura en la nube
description: En este tema se analiza una solución cuando la carga alta de MySQL causa un problema de cuello de botella de rendimiento en Adobe Commerce en la infraestructura en la nube.
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Cuello de botella de carga alta MySQL en Adobe Commerce en la infraestructura en la nube

En este tema se analiza una solución cuando la carga alta de MySQL causa un problema de cuello de botella de rendimiento en Adobe Commerce en la infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube 2.x.x, cuentas Pro.

### Requisitos previos

* ECE Tools versión 2002.0.16 y superior
* Servicio de APM de New Relic (**Su cuenta de Adobe Commerce en la infraestructura de la nube incluye el software para el servicio de APM de New Relic** junto con una clave de licencia.)

Para obtener más información sobre el servicio APM de New Relic y su configuración con su cuenta de Adobe Commerce en la infraestructura de la nube, vaya a [Servicios de New Relic](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service) e [Introducción a APM de New Relic](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## Problema

<u>Pasos Para Ver Si El Problema Te Afecta</u>

1. En el gráfico de información general de APM de New Relic, compruebe si hay la primera indicación de que MySQL se ha convertido en un cuello de botella. Vea la siguiente imagen de muestra donde MySQL se ha convertido en un cuello de botella y toma la mayoría del tiempo de las transacciones web:

   ![KB-372_image002.png](assets/KB-372_image002.png)

   Observe cómo la línea roja discontinua en la imagen muestra una tendencia ascendente perceptible en el tiempo de transacciones web de MySQL y luego alcanza picos en niveles aún más altos.
1. Desde aquí puede ir a la pantalla de **Base de datos**, donde puede ver la segunda indicación de alto rendimiento o `SELECT` consultas lentas en MySQL, y en la siguiente imagen de muestra puede ver al ordenar por **Más tiempo que consume**, su tienda, en este ejemplo, es lenta en `SELECT` consultas MySQL.

   ![KB-372_image003_BlurredExtension.png](assets/KB-372_image003_BlurredExtension.png)

Analice las transacciones lentas en New Relic APM. Si ve un gran volumen de consultas o una alta presión en una base de datos MySQL, puede distribuir la carga entre diferentes nodos habilitando `SLAVE` conexiones.

## Causa

El almacén de Adobe Commerce en la infraestructura de la nube tiene un alto rendimiento o es lento en `SELECT` consultas MySQL.

## Solución

>[!WARNING]
>
>Para la arquitectura escalada (arquitectura dividida), las conexiones esclavas de Redis **NO DEBERÍAN** habilitarse. Para comprobar si su arquitectura está escalada, vaya a la dirección URL de su proyecto, p. ej. `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`. Haga clic en **[!UICONTROL SSH]**. Si hay más de tres nodos, se utiliza la arquitectura a escala. Si habilita Lecturas esclavas de Redis en la arquitectura escalada, el cliente recibirá errores en las conexiones de Redis que no puedan conectarse. Esto tiene que ver con la configuración de los clústeres para procesar las conexiones de Redis. Los Esclavos de Redis siguen activos, pero no se usarán para Redis Reads. Recomendamos que la arquitectura escalada use Adobe Commerce 2.3.5 o posterior e implemente la nueva configuración back-end de Redis e implemente el almacenamiento en caché L2 para Redis.

Si se experimentan estas dos indicaciones, habilitar las conexiones de `SLAVE` para la base de datos MySQL y Redis puede ayudar a distribuir la carga entre nodos diferentes.

Adobe Commerce puede leer varias bases de datos o Redis de forma asíncrona. Actualizando el archivo `.magento.env.yaml` estableciendo en `true` los valores `MYSQL_USE_SLAVE_CONNECTION` y `REDIS_USE_SLAVE_CONNECTION` para utilizar una conexión de **solo lectura** con la base de datos para recibir tráfico de solo lectura en un nodo no maestro. Esto mejora el rendimiento mediante el equilibrio de carga, ya que solo un nodo necesita gestionar el tráfico de lectura-escritura. Establezca el valor en `false` para quitar cualquier matriz de conexión de solo lectura existente del archivo `env.php`.

### Pasos

1. Edite su archivo de `.magento.env.yaml` y agregue el siguiente contenido:

   ![KB-372_image004.png](assets/KB-372_image004.png)

   Puede encontrar más detalles en [Implementar variables en DevDocs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection).

1. Confirme los cambios e inserte los cambios.
1. La inserción de cambios iniciará un nuevo proceso de implementación. Una vez completada correctamente la implementación, debe configurar la instancia de Adobe Commerce en la infraestructura en la nube para que utilice conexiones esclavas.

## Preguntas comunes

A continuación se muestran las preguntas comunes que puede hacerse al considerar el uso de la funcionalidad de conexiones esclavas para su Adobe Commerce en el almacén de infraestructura en la nube.

* ¿Hay algún problema o limitación conocidos para utilizar conexiones esclavas? **No tenemos ningún problema conocido relacionado con el uso de conexiones esclavas. Solo asegúrese de que está utilizando el paquete ece-tools actualizado más recientemente. Las instrucciones están aquí en [cómo actualizar el paquete ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package).**
* ¿Existe latencia adicional al utilizar conexiones esclavas? *Sí, la latencia entre AZ (zonas de disponibilidad cruzada) es mayor y reduce el rendimiento de una Adobe Commerce en una instancia de infraestructura en la nube en el caso de que la instancia no esté sobrecargada y pueda llevar toda la carga. Pero claramente, si la instancia está sobrecargada, maestro-esclavo ayudará con el rendimiento al distribuir la carga en la base de datos MySQL o Redis en diferentes nodos.*

  **En clústeres no sobrecargados** - **Las conexiones esclavas ralentizarán el rendimiento en un 10-15%**, una de las razones por las que no es predeterminado.

  *Pero en los clústeres sobrecargados, hay un aumento de rendimiento porque estos 10-15% se reducen reduciendo la carga por el tráfico.*
* ¿Debo habilitar esta configuración para mi tienda? *Si tiene una carga alta o espera una carga alta en la base de datos MySQL o en Redis, definitivamente necesita habilitar Slave Connections. Para un cliente normal con tráfico promedio,**no**&#x200B;es una configuración óptima para habilitarlo.*

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [Implementar variables](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy).
* [Configurar replicación opcional de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master-replication).
* [paquete ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview).

>[!NOTE]
>
>Somos conscientes de que este artículo aún puede contener términos de software estándar en la industria que algunos pueden encontrar racistas, sexistas u opresivos, y que pueden hacer que el lector se sienta herido, traumatizado o no deseado. El Adobe de está trabajando para eliminar estos términos de nuestro código, documentación y experiencias de usuario.
