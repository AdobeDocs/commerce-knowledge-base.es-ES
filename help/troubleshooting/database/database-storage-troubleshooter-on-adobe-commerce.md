---
title: Solucionador de problemas de almacenamiento de bases de datos en Adobe Commerce
description: Este artículo es una herramienta para solucionar problemas de los clientes de Adobe Commerce que tienen problemas con las bases de datos de. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas. Según los síntomas y la configuración, el solucionador de problemas explicará cómo solucionar problemas de espacio y configuración con las bases de datos.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Solucionador de problemas de almacenamiento de bases de datos en Adobe Commerce

Este artículo es una herramienta para solucionar problemas de los clientes de Adobe Commerce que tienen problemas con las bases de datos de. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas. Según los síntomas y la configuración, el solucionador de problemas explicará cómo solucionar problemas de espacio y configuración con las bases de datos.

## Paso 1: Identificación del directorio con un problema de espacio {#step-1}

+++**¿Tiene un `/tmp` problema causado por la falta de espacio?**

Esto puede estar indicado por una serie de síntomas, incluyendo `/tmp` el montaje está lleno, el sitio está caído o no se puede SSH en un nodo. También es posible que esté experimentando errores como _No queda espacio en el dispositivo (28)_. Para obtener una lista de los errores resultantes de `/tmp` estar lleno, revisar [/tmp montaje completo](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

¿O tiene una `/data/mysql` problema causado por la falta de espacio? Esto también se puede indicar por una variedad de síntomas, incluida la interrupción del sitio, los clientes que no pueden agregar productos al carro de compras, los errores de conexión a la base de datos y los errores de GALERIA como _SQLSTATE\[08S01\]: Error de vínculo de comunicación: 1047 WSREP_. Para obtener una lista de errores resultantes de un espacio en disco MySQL bajo, consulte [El espacio en disco de MySQL es bajo en Adobe Commerce en la infraestructura en la nube](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Si no está seguro de tener un problema de espacio en disco y tiene una cuenta de New Relic, vaya a [Página Hosts de Monitorización de Infraestructura de New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). A partir de ahí, haga clic en **Almacenamiento** pestaña, cambie la **El gráfico muestra** desplegable de 5 a 20 resultados y busque en la tabla un alto uso de disco en el gráfico o tabla % de disco usado. Para ver los pasos más detallados, consulte [Pestaña Monitorización de infraestructura de New Relic > Almacenamiento]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Si tiene alguno de los síntomas descritos anteriormente, compruebe el estado de sus inodes para asegurarse de que esto no esté siendo causado por un problema de número de archivo. Para ello, ejecute el siguiente comando en CLI/Terminal:\
`df -ih`

¿Es IUse% > 90%?

a. SÍ: esto se debe a que tiene demasiados archivos. Revise los pasos para eliminar archivos de forma segura en [Elimine los archivos de forma segura cuando se agote el espacio en disco, Adobe Commerce en la infraestructura en la nube](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Continúe en [Paso 2](#step-2) después de completar estos pasos. Si desea solicitar más espacio, [enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Compruebe el espacio. Ejecutar `df -h | grep mysql` y luego `df -h | grep tmp` en CLI/Terminal para comprobar el uso del espacio en disco en `/tmp` y `/data/mysql` directorios. Continúe en [Paso 3](#step-3).

+++

## Paso 2: Comprobación del espacio en disco {#step-2}

+++**¿Comprobar el uso del espacio en disco?**

Una vez reducido el número de archivos, ejecute `df -h | grep mysql` y luego `df -h | grep tmp` en CLI/Terminal para comprobar el uso del espacio en disco en `/tmp` y `/data/mysql`. Es mayor que el 70 % utilizado para `/tmp` o `/data/mysql`?

a. SÍ: Continúe con [Paso 3](#step-3).
b. NO - Las consultas pueden estar agotando el almacenamiento disponible. Esto puede bloquear el nodo, desactivando la consulta y eliminando el `tmp` archivos. Examine el resultado del `SHOW PROCESSLIST;` en la CLI de MySQL para consultas que puedan ser la causa del problema. [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando más espacio.

+++

## Paso 3: Identificar el directorio con un uso elevado {#step-3}

+++**¿Qué directorio utiliza más del 70 %?**

¿Qué directorio utiliza más del 70 %? `/tmp` o `/data/mysql`?

>[!NOTE]
>
>De forma predeterminada, la base de datos tmpdir escribe en `/tmp`. Para comprobar que la configuración de la base de datos sigue siendo la predeterminada, ejecute el siguiente comando en la CLI de MySQL: `SHOW VARIABLES LIKE "TMPDIR";` Si el tmpdir de la base de datos sigue escribiendo en `/tmp`, verá lo siguiente `/tmp` en la columna Value.

a. `/tmp` - Continúe con [Paso 4](#step-4). \
b. `/data/mysql` - Continúe con [Paso 5](#step-5).

+++

## Paso 4: Solución de problemas del montaje /tmp completo {#step-4}

+++**Solucionar problemas del montaje /tmp completo**

[Solucionar problemas del montaje completo de /tmp para Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), desplácese hacia abajo por el artículo y pruebe las soluciones y prácticas recomendadas. Entonces ejecute `df -h | grep mysql` y luego `df -h | grep tmp` en CLI/Terminal para comprobar el uso del espacio en disco en `/tmp` y `/data/mysql` directorios\
  ¿Usado &lt; 70%?

>[!NOTE]
>
>Las soluciones de [Solucionar problemas del montaje completo de /tmp para Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) están diseñadas para comerciantes que no han cambiado las variables para el tmpdir de la base de datos, que de forma predeterminada escribe en `/tmp`. Si ha cambiado el valor tmpdir, las instrucciones de [Solucionar problemas del montaje completo de /tmp para Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) no ayudará.

a. SÍ - Ha resuelto el problema. \
b. NO - [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando más espacio.

+++

## Paso 5: Comprobación del valor predeterminado {#step-5}

+++**Comprobar predeterminado**

Es posible que la configuración de la base de datos ya no sea la predeterminada original. Busque la configuración tmpdir de la base de datos ejecutando en la CLI de MySQL: `SELECT @@DATADIR;`. If `/data/mysql/` se obtiene, el tmpdir de la base de datos está escribiendo en `/data/mysql/`. Intente aumentar el espacio en este directorio siguiendo los pasos indicados en [El espacio en disco de MySQL es bajo en Adobe Commerce en nuestra infraestructura en la nube](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Entonces ejecute `df -h | grep mysql` y luego `df -h | grep tmp` en CLI/Terminal para comprobar el uso del espacio en disco en `/data/mysql` y `/tmp`.\
  ¿Usado &lt; 70%?

a. SÍ - Ha resuelto el problema. \
b. NO - [Enviar un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando más espacio.

+++

[Volver al paso 1](#step-1)
