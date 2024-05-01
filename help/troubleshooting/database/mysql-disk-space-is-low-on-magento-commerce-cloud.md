---
title: El espacio en disco de MySQL es bajo en Adobe Commerce en la infraestructura en la nube
description: Este artículo proporciona soluciones para cuando está experimentando un espacio muy bajo o ningún espacio para MySQL en Adobe Commerce en la infraestructura en la nube. Los síntomas pueden incluir interrupciones del sitio, clientes que no pueden añadir productos al carro de compras, que no pueden conectarse a la base de datos, que no pueden acceder a la base de datos de forma remota, que no pueden SSH en el nodo. Los síntomas también incluyen errores de Galera, sincronización del entorno, PHP, base de datos e implementación, como se indica a continuación. Haga clic en [Solución](https://support.magento.com/hc/en-us/articles/360058472572#solution) para saltar directamente a la sección de la solución.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# El espacio en disco de MySQL es bajo en Adobe Commerce en la infraestructura en la nube

Este artículo proporciona soluciones para cuando está experimentando un espacio muy bajo o ningún espacio para MySQL en Adobe Commerce en la infraestructura en la nube. Los síntomas pueden incluir interrupciones del sitio, clientes que no pueden añadir productos al carro de compras, que no pueden conectarse a la base de datos, que no pueden acceder a la base de datos de forma remota, que no pueden SSH en el nodo. Los síntomas también incluyen errores de Galera, sincronización del entorno, PHP, base de datos e implementación, como se indica a continuación. Clic [Solución](https://support.magento.com/hc/en-us/articles/360058472572#solution) para ir directamente a la sección de solución.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problema

La base de datos es demasiado grande. Los síntomas pueden incluir la pérdida de la conexión a la base de datos, un error de carga de la base de datos y una serie de otros problemas.

Errores que pueden producirse:

Galera:

* *SQLSTATE\[08S01\]: Error de vínculo de comunicación: WSREP 1047 aún no ha preparado el nodo para el uso de la aplicación*   *Errores de importación:*
* *SQLSTATE\[HY000\]: Error general: 1180 Se obtuvo el error 5 &quot;Error de entrada/salida&quot;*
* *SQLSTATE\[08S01\]: Error de vínculo de comunicación: WSREP 1047 aún no ha preparado el nodo para el uso de la aplicación*

Errores de sincronización de entorno:

* *SQLSTATE: Error general: 1180 Se obtuvo el error 5 &quot;Error de entrada/salida&quot; durante la confirmación*

Errores de PHP:

* *php: PDO::\_\_builds(): El servidor MySQL ha desaparecido.*
* *php errors: PDO::\_\_builds(): Error al leer el paquete de saludo. PID=NNNN.*
* *ERROR 2013 (HY000): Se perdió la conexión con el servidor MySQL en &#39;leer el paquete de comunicación inicial&#39;, error del sistema: 0 &quot;Error interno/comprobación (no error del sistema)&quot;.*

Errores de base de datos:

* *Error\_code: 1114*
* *InnoDB: Error (espacio en disco insuficiente) al escribir el nodo de Word en la tabla de índice auxiliar de FTS.*
* *SQLSTATE\[HY000\]: Error general: 2006 El servidor MySQL ha desaparecido*
* *\[ERROR\] SQL esclavo: Error &#39;La tabla `<table\_name>` está lleno&#39; en la consulta.*
* *La unidad mysql.service ha introducido el estado de error.*
* *error: &#39;No se puede conectar al servidor MySQL local a través del socket &#39;/var/run/mysqld/mysqld.sock&#39; (111 &quot;Conexión rechazada&quot;)&#39;*
* *1205 Se ha superado el tiempo de espera de bloqueo; intente reiniciar la transacción, la consulta era: INSERT INTO \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) VALORES (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Errores de implementación:

* *E: Comando &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; devolvió un estado de salida distinto de cero 255*
* *E: Comando &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 reiniciar sitio-`<environment name>`g-nginx&#39;\]&#39; devolvió un valor distinto de cero*
* *Actualizando esquema.. SQLSTATE\[HY000\]: Error general: 1114 La tabla `<table\_name>` está lleno*
* *SQLSTATE\[HY000\]: Error general: 3 Error al escribir el archivo ./`<environment name>`/\#*
* *A: `<filename>` (Código de error: 28 &quot;No queda espacio en el dispositivo&quot;)*  *Errores de indexación (junto con archivos temporales .ibd huérfanos en /tmp):*
* *El indexador de reglas de catálogo genera una excepción. Las tablas temporales no se limpian después y luego llenan el disco en el nodo maestro MySQL actual*

<u>Pasos a seguir</u>:

Una de las formas de comprobar si la variable `/data/mysql` (o siempre que el almacenamiento de datos MySQL esté configurado) esté lleno se ejecuta ejecutando el siguiente comando en la CLI:

```bash
df -h
```

Menos del 10% de la memoria libre en el disco MySQL es un indicador principal de una interrupción.

## Causa

El `/data/mysql` mount puede llenarse debido a una serie de problemas, como no tener suficientes inodes, espacio de almacenamiento disponible y consultas incorrectas que generan tablas temporales.

## Solución

Hay un paso inmediato que podría tomar para volver a poner MySQL en marcha (o evitar que se atasque): libere algo de espacio vaciando las tablas grandes.

Pero una solución a largo plazo sería asignar más espacio y seguir [Prácticas recomendadas de base de datos](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html), incluida la activación de [Archivo de pedido/factura/envío](https://docs.magento.com/user-guide/sales/order-archive.html) funcionalidad.

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

### Comprobar si hay grandes `ibtmp1` archivos

Comprobar si hay grandes `ibtmp1` archivo en `/data/mysql` de cada nodo: este archivo es el tablespace para las tablas temporales. Si hay consultas incorrectas que generan tablas temporales, se incluyen en la variable `ibtmp1` archivo. Este archivo sólo se quita cuando se reinicia la base de datos. Si ocupa todo el espacio disponible, debe reiniciarse la base de datos. Si hay consultas incorrectas, se volverá a crear.

### Vaciar las mesas grandes

>[!WARNING]
>
>Se recomienda encarecidamente crear una copia de seguridad de la base de datos antes de realizar cualquier manipulación y evitarlas durante períodos de carga alta del sitio. Consulte [Volcar la base de datos](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump) en nuestra documentación para desarrolladores.

Compruebe si hay tablas grandes y considere si alguna de ellas se puede vaciar. Haga esto en el nodo principal (origen).

Por ejemplo, las tablas con informes suelen vaciarse. Para obtener más información sobre cómo buscar tablas grandes, consulte la [Buscar tablas MySQL grandes](/help/how-to/general/find-large-mysql-tables.md) artículo.

Si no hay tablas de informes enormes, considere la posibilidad de vaciar `_index` , solo para volver a encarrilar la aplicación de Adobe Commerce. `index_price` Las mesas serían los mejores candidatos. Por ejemplo, `catalog_category_product_index_storeX` , donde X puede tener valores desde &quot;1&quot; hasta el número máximo de almacenes. Tenga en cuenta que deberá reindexar para restaurar los datos de estas tablas y, en el caso de catálogos grandes, este reindexado puede llevar mucho tiempo.

Una vez vaciados, espere a que finalice la sincronización de wsrep. Ahora puede crear copias de seguridad y realizar pasos más significativos para añadir más espacio, como asignar o comprar más espacio y habilitar [Archivo de pedido/factura/envío](https://docs.magento.com/user-guide/sales/order-archive.html) funcionalidad.

### Comprobar configuración de registro binario

Compruebe la configuración del registro binario del servidor MySQL: `log_bin` y `log_bin_index`. Si la configuración está habilitada, los archivos de registro pueden llegar a ser enormes. [Creación de una solicitud de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando purgar archivos de registro binarios grandes. Además, solicite comprobar que el registro binario se está configurando correctamente para que los registros se purguen periódicamente y no ocupen demasiado espacio.

Si no tiene acceso a la configuración del servidor MySQL, solicite asistencia técnica para comprobarlo.

### Asignar/comprar más espacio

Asigne más espacio en disco para MySQL si tiene algo sin usar. Consulte la [Comprobar límite de espacio en disco](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) artículo para aprender a comprobar si tiene espacio libre en disco.

* Para el plan de inicio, todos los entornos y los entornos de integración del plan Pro, puede asignar el espacio en disco si no lo ha utilizado. Para obtener más información, consulte la [Asignar más espacio para MySQL](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Para entornos de ensayo y producción de plan Pro, [soporte de contacto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para asignar más espacio en disco si no se ha utilizado.

Si ha alcanzado el límite de espacio y sigue experimentando problemas de poco espacio, considere la posibilidad de comprar más espacio en disco, póngase en contacto con el equipo de cuenta de Adobe para obtener más información.
