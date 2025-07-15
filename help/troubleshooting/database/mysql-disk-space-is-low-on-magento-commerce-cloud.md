---
title: '[!DNL MySQL] espacio en disco es bajo en Adobe Commerce en la infraestructura de la nube'
description: Este artículo proporciona soluciones para situaciones en las que experimentas poco espacio o ningún espacio para  [!DNL MySQL] en Adobe Commerce en la infraestructura en la nube. Los síntomas pueden incluir interrupciones del sitio, clientes que no pueden añadir productos al carro de compras, que no pueden conectarse a la base de datos, que no pueden acceder a la base de datos de forma remota, que no pueden SSH en el nodo. Los síntomas también incluyen errores de Galera, sincronización del entorno, PHP, base de datos e implementación, como se indica a continuación. Haga clic en [Solución](https://support.magento.com/hc/en-us/articles/360058472572#solution) para saltar directamente a la sección de la solución.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 80343c834563e7550569d225979edfa6a997bcfc
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 0%

---

# [!DNL MySQL] espacio en disco es bajo en Adobe Commerce en la infraestructura de la nube

Este artículo proporciona soluciones para situaciones en las que experimenta muy poco espacio o ningún espacio para [!DNL MySQL] en Adobe Commerce en la infraestructura en la nube. Los síntomas incluyen interrupciones del sitio, clientes que no pueden añadir productos al carro de compras, que no pueden conectarse a la base de datos, que no pueden acceder a la base de datos de forma remota, que no pueden SSH en el nodo. Los síntomas también incluyen errores de Galera, sincronización del entorno, PHP, base de datos e implementación, como se indica a continuación. Haga clic en [Solución](https://support.magento.com/hc/en-us/articles/360058472572#solution) para saltar directamente a la sección de la solución.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problema

La base de datos es demasiado grande. Los síntomas pueden incluir la pérdida de la conexión a la base de datos, un error de carga de la base de datos y una serie de otros problemas.

Errores que pueden producirse:

Galera:

* *SQLSTATE\[08S01\]: error de vínculo de comunicación: WSREP 1047 aún no ha preparado el nodo para el uso de la aplicación*   *Errores de importación:*
* *SQLSTATE\[HY000\]: Error general: 1180 Se obtuvo el error 5 &quot;Error de entrada/salida&quot;*
* *SQLSTATE\[08S01\]: error de vínculo de comunicación: WSREP 1047 aún no ha preparado el nodo para el uso de la aplicación*

Errores de sincronización de entorno:

* *SQLSTATE: Error general: 1180 Se obtuvo el error 5 &quot;Error de entrada/salida&quot; durante la confirmación*

Errores de PHP:

* *php: PDO::\_\_builds(): el servidor [!DNL MySQL] ha desaparecido.*
* *errores php: PDO::\_\_builds(): Error al leer el paquete de saludo. PID=NNNN.*
* *ERROR 2013 (HY000): Se perdió la conexión con el servidor [!DNL MySQL] al &#39;leer el paquete de comunicación inicial&#39;, error del sistema: 0 &quot;Error interno/comprobación (no error del sistema)&quot;.*

Errores de base de datos:

* *Error\_code: 1114*
* *InnoDB: error (espacio en disco insuficiente) al escribir el nodo de Word en la tabla de índice auxiliar de FTS.*
* *SQLSTATE\[HY000\]: Error general: el servidor [!DNL MySQL] de 2006 ha desaparecido*
* *\[ERROR\] SQL esclavo: Error &#39;La tabla `<table\_name>` está llena&#39; en la consulta.*
* *El mysql.service de la unidad entró en estado de error.*
* *error: &#39;No se puede conectar al servidor local [!DNL MySQL] a través del socket &#39;/var/run/mysqld/mysqld.sock&#39; (111 &quot;Conexión rechazada&quot;)&#39;*
* *1205 Se superó el tiempo de espera de bloqueo; intente reiniciar la transacción. La consulta era: INSERT INTO \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) VALUES (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Errores de implementación:

* *E: el comando &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; devolvió un estado de salida distinto de cero 255*
* *E: el comando &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 sitio de reinicio-`<environment name>`g-nginx&#39;\]&#39; devolvió un valor distinto de cero*
* *Actualizando esquema.. SQLSTATE\[HY000\]: Error general: 1114 La tabla `<table\_name>` está llena*
* *SQLSTATE\[HY000\]: Error general: 3 Error al escribir el archivo ./`<environment name>`/\#*
* *W: `<filename>` (código de error: 28 &quot;No queda espacio en el dispositivo&quot;)* *Errores de indexación (junto con archivos temporales .ibd huérfanos en /tmp):*
* El indizador de reglas de catálogo *genera una excepción. Las tablas temporales no se limpian después y luego llenan el disco en el nodo maestro [!DNL MySQL] actual*

<u>Pasos a seguir</u>:

Una de las formas en que puede comprobar si el `/data/mysql` (o donde esté configurado el almacenamiento de datos [!DNL MySQL]) está lleno es ejecutando el siguiente comando en la CLI:

```bash
df -h
```

Menos del 10% de la memoria libre en el disco [!DNL MySQL] es un indicador principal de una interrupción.

## Causa

Es posible que el montaje de `/data/mysql` se llene debido a una serie de problemas, como no tener suficientes nodos, espacio de almacenamiento disponible y consultas incorrectas que generan tablas temporales.

## Solución

Hay un paso inmediato que podría tomar para volver a encauzar [!DNL MySQL] (o evitar que se atasque): libere espacio vaciando las tablas grandes.

Sin embargo, una solución a largo plazo sería asignar más espacio y seguir las [prácticas recomendadas de la base de datos](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=es), incluida la habilitación de la funcionalidad [Archivo de pedidos/facturas/envíos](https://experienceleague.adobe.com/es/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

A continuación se ofrecen detalles sobre soluciones rápidas y a largo plazo.

### Comprobación y liberación de inodes

Asegúrese de que haya suficientes nodos disponibles. Para ello, ejecute el siguiente comando:

```bash
df -i
```

El resultado sería similar al siguiente:

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Compruebe que % de uso es &lt;70 %. Los nodos se correlacionan con los archivos. Si elimina archivos de la partición, liberará inodes.

### Compruebe y libere espacio de almacenamiento

Compruebe el espacio de almacenamiento disponible. Para ello, ejecute:

```bash
df -k
```

El resultado sería similar al siguiente:

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

Si el porcentaje de uso es >70 %, debe realizar alguna acción para liberar o agregar espacio.

### Buscar `ibtmp1` archivos grandes

Compruebe el archivo `ibtmp1` grande en `/data/mysql` de cada nodo: este archivo es el tablespace para las tablas temporales. Si hay consultas erróneas que generan tablas temporales, se encuentran en el archivo `ibtmp1`. Este archivo sólo se quita cuando se reinicia la base de datos. Si ocupa todo el espacio disponible, debe reiniciarse la base de datos. Si hay consultas incorrectas, se volverá a crear.

### Vaciar las mesas grandes

>[!WARNING]
>
>Se recomienda encarecidamente crear una copia de seguridad de la base de datos antes de realizar cualquier manipulación y evitarlas durante períodos de carga alta del sitio. Consulte [Volcar la base de datos](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) en nuestra documentación para desarrolladores.

Compruebe si hay tablas grandes y considere si alguna de ellas se puede vaciar. Haga esto en el nodo principal (origen).

Por ejemplo, las tablas con informes suelen vaciarse. Para obtener más información sobre cómo buscar tablas grandes, consulte el artículo [Buscar tablas grandes [!DNL MySQL] 2&rbrace;.](/help/how-to/general/find-large-mysql-tables.md)

Si no hay tablas de informes enormes, considere la posibilidad de vaciar `_index` tablas, solo para volver a encarrilar la aplicación de Adobe Commerce. `index_price` tablas serían los mejores candidatos. Por ejemplo, `catalog_category_product_index_storeX` tablas, donde X puede tener valores desde &quot;1&quot; hasta el número máximo de tiendas. Tenga en cuenta que deberá reindexar para restaurar los datos de estas tablas y, en el caso de catálogos grandes, este reindexado puede llevar mucho tiempo.

Una vez vaciados, espere a que finalice la sincronización de wsrep. Ahora puede crear copias de seguridad y realizar pasos más significativos para agregar más espacio, como asignar o comprar más espacio y habilitar la funcionalidad [Archivo de pedidos/facturas/envíos](https://experienceleague.adobe.com/es/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

### Comprobar configuración de registro binario

Compruebe la configuración del registro binario del servidor [!DNL MySQL]: `log_bin` y `log_bin_index`. Si la configuración está habilitada, los archivos de registro pueden llegar a ser enormes. [Crear un ticket de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando purgar archivos de registro binarios grandes. Además, solicite comprobar que el registro binario se está configurando correctamente para que los registros se purguen periódicamente y no ocupen demasiado espacio.

Si no tiene acceso a la configuración del servidor [!DNL MySQL], solicite asistencia técnica para comprobarlo.

### Recuperar espacio en disco asignado no utilizado

1. SSH en el nodo uno e inicie sesión en MySQL:

   ```sh
   mysql -h127.0.0.1 -p`php -r "echo (include('app/etc/env.php'))['db']['connection']['default']['password'];"` -u`whoami` `whoami`
   ```

   Para ver los pasos detallados, consulte [Conectar y ejecutar consultas en la base de datos de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-learn/tutorials/backend-development/remote-db-connection-execute-queries).

1. Compruebe si hay espacio sin utilizar:

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) AS size_MB, round((data_free)/1048576,2) AS Allocated_but_unused FROM information_schema.tables WHERE data_free > 1048576*10 ORDER BY data_free DESC;
   ```


   Ejemplo de salida:

   | table_name | size_MB | Asignado_pero_no utilizado |
   |----------------------|----------|--------------------------|
   | vertex_taxrequest | 28145,20 | 14943,00 |


   Compruebe la salida para ver si hay memoria que se haya asignado pero que no se haya utilizado. Esto ocurre cuando los datos se han eliminado de una tabla; sin embargo, la memoria aún está asignada a esa tabla.


1. Coloque el sitio en modo de mantenimiento y detenga los trabajos cron para que no se produzcan interacciones en la base de datos. Para ver los pasos, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) y [Deshabilitar los trabajos cron](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).
1. Recupere ese espacio volviendo a crear la tabla utilizando el siguiente comando (por ejemplo, utilizando la tabla anterior con el espacio más utilizado):

   ```sql
   ALTER TABLE vertex_taxrequest Engine = "INNODB";
   ```

1. Ejecute la siguiente consulta para comprobar si hay espacio sin asignar para cada tabla que muestre un valor alto dentro de la columna **[!UICONTROL Allocated_but_unused]**.

   ```sql
   SELECT table_name, round((data_length+index_length)/1048576,2) as size_MB, round((data_free)/1048576,2) as Allocated_but_unused FROM information_schema.tables WHERE 1 AND data_free > 1048576*10 ORDER BY 
   data_free DESC;
   ```


1. Ahora [Deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#enable-or-disable-maintenance-mode-1) y [Habilitar trabajos cron](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property#disable-cron-jobs).


### Asignar/comprar más espacio

Asigne más espacio en disco para [!DNL MySQL] si no utiliza alguno. Consulte el artículo [Comprobar el límite de espacio en disco](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) para saber cómo comprobar si tiene espacio libre en disco.

* Para el plan de inicio, todos los entornos y los entornos de integración del plan Pro, puede asignar el espacio en disco si no lo ha utilizado. Para obtener más información, consulta [Asignar más espacio para [!DNL MySQL]](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Para los entornos de ensayo y producción del plan Pro, [póngase en contacto con el servicio de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para asignar más espacio en disco si tiene espacio sin usar.

Si ha alcanzado el límite de espacio y sigue experimentando problemas de poco espacio, considere la posibilidad de comprar más espacio en disco, póngase en contacto con el equipo de cuenta de Adobe para obtener más información.

## Lectura relacionada

[Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
