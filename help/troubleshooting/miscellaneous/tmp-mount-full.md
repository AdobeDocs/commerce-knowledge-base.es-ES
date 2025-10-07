---
title: Solucionar problemas del montaje completo de /tmp para Adobe Commerce
description: Este artículo proporciona una solución para cuando el montaje /tmp está lleno, el sitio puede estar caído y no puede SSH en un nodo.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: aa4cfbceb745f1a06b8a8f9e93cbdebbc151458b
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Solucionar problemas del montaje completo de /tmp para Adobe Commerce

Este artículo proporciona una solución para cuando el montaje de `/tmp` esté lleno, el sitio pueda estar caído y no pueda SSH en un nodo.

## Productos y versiones afectados

* Adobe Commerce 2.3.0: 2.3.6-p1, 2.4.0: 2.4.2

## Problema

Si el montaje `/tmp` está lleno, es posible que aparezcan varios síntomas, incluidos los siguientes errores:

* *SQLSTATE[HY000]: Error general: 3 Error al escribir el archivo*
* *Código de error: 28*
* *No queda espacio en el dispositivo (28)*
* *error session_start(): error: no queda espacio en el dispositivo*
* *ERROR 1 (HY000): no se puede crear/escribir en el archivo &#39;/tmp/*
* *Error de SQL: 3, SQLState: HY000*
* *Error general: disco 1021 lleno (/tmp)*
* *No se puede obtener acceso al nodo a través de SSH:*
  *bash: no se puede crear el archivo temporal para aquí-documento: no queda espacio en el dispositivo*
* *error: 28 &quot;No queda espacio en el dispositivo&quot;*
* *mysqld: el disco está escribiendo por completo &#39;/tmp&#39;*
* *[ERROR] mysqld: Disco lleno (/tmp)*
* *SQLSTATE[HY000]: Error general: 1 No se puede crear/escribir en el archivo &#39;/tmp/&#39;*
* *SQLSTATE[HY000]: Error general: 23 Recursos insuficientes al abrir el archivo &#39;/tmp/&#39;*
* *Código de error: 24 &quot;Demasiados archivos abiertos&quot;*
* *Error obtenido: 23: Recursos insuficientes al abrir el archivo*


<u>Pasos a seguir:</u>

Para comprobar el grado de llenado del montaje `/tmp`, en la CLI cambie a `/tmp` y ejecute el siguiente comando:

```bash
 df -h
```

<u>Resultado esperado</u>:

Menos del 80%.

<u>Resultado real</u>:

Alrededor del 100%.

## Causa

El montaje de `/tmp` tiene demasiados archivos, lo que podría deberse a lo siguiente:

* Consultas SQL incorrectas que generan tablas temporales grandes o demasiadas.
* Servicios escribiendo en el directorio `/tmp`.
* Copias de seguridad/volcados de base de datos restantes en el directorio `/tmp`.

## Solución

Hay cosas que puede hacer para liberar espacio una vez y hay prácticas recomendadas que evitarían que `\tmp` se llenara.

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

Compruebe que Use% sea &lt;70%. Los nodos se correlacionan con los archivos. Si elimina archivos de la partición, liberará inodes.

### Compruebe y libere espacio de almacenamiento

Hay varios servicios que podrían estar guardando archivos en `/tmp`.

#### Comprobar y liberar espacio en MySQL

Siga las instrucciones de [MySQL disk space is low on Adobe Commerce on cloud Infrastructure > Compruebe y libere espacio de almacenamiento](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-27806#check-and-free-up-storage-space) en nuestra base de conocimiento de asistencia.

#### Compruebe los volcados de pila de Elasticsearch

>[!WARNING]
>
>Los volcados de la pila contienen información de registro que puede ser útil para investigar problemas. Considere la posibilidad de almacenarlas en un lugar separado durante al menos 10 días.

Elimine los volcados de la pila (`*.hprof`) mediante el shell del sistema:

```bash
find /tmp/*.hprof -type f -delete
```

Si no tiene permisos para eliminar archivos creados por otro usuario (en este caso, Elasticsearch), pero ve que los archivos son grandes, [cree un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para encargarse de ellos.

#### Comprobar volcados/copias de seguridad de base de datos

>[!WARNING]
>
>Las copias de seguridad de bases de datos suelen crearse con un propósito. Si no está seguro de si el archivo sigue siendo necesario, considere la posibilidad de moverlo a una ubicación independiente en lugar de eliminarlo.

Busque `/tmp` archivos de `.sql` o `.sql.gz` y límpielos. Es posible que se hayan creado mediante ece-tools durante la copia de seguridad o al crear manualmente volcados de base de datos con la herramienta `mysqldump`.

### Prácticas recomendadas

Para evitar problemas con `/tmp`, siga estas recomendaciones:

* No utilice MySQL para la búsqueda. Elasticsearch para la búsqueda generalmente elimina la necesidad de la mayoría de las creaciones de tablas temporales pesadas. Consulte [Configuración de Adobe Commerce para usar Elasticsearch](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/search/configure-search-engine) en nuestra documentación para desarrolladores.
* Evite ejecutar la consulta `SELECT` en columnas sin índices, ya que esto consume una gran cantidad de espacio temporal en disco. También puede añadir los índices.
* Cree un cron para limpiar `/tmp` ejecutando el siguiente comando en la CLI:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Lectura relacionada

[El espacio en disco de MySQL es bajo en Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-27806) en nuestra base de conocimiento de soporte.
