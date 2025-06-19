---
title: Solucionador de problemas de almacenamiento de bases de datos en Adobe Commerce
description: Este artículo es una herramienta para solucionar problemas de los clientes de Adobe Commerce que tienen problemas con las bases de datos de. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas. Según los síntomas y la configuración, el solucionador de problemas explicará cómo solucionar problemas de espacio y configuración con las bases de datos.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Solucionador de problemas de almacenamiento de bases de datos en Adobe Commerce

Este artículo es una herramienta para solucionar problemas de los clientes de Adobe Commerce que tienen problemas con las bases de datos de. Haga clic en cada pregunta para mostrar la respuesta en cada paso del solucionador de problemas. Según los síntomas y la configuración, el solucionador de problemas explicará cómo solucionar problemas de espacio y configuración con las bases de datos.

## Paso 1: Identificación del directorio con un problema de espacio {#step-1}

+++**¿Tiene un problema de `/tmp` debido a la falta de espacio?**

Esto se puede indicar por una serie de síntomas, incluyendo que el montaje `/tmp` esté lleno, que el sitio esté caído o que no pueda insertarse SSH en un nodo. También puede estar experimentando errores como _No queda espacio en el dispositivo (28)_. Para obtener una lista de errores resultantes de que `/tmp` esté lleno, revise [/tmp mount full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

¿O tiene un problema de `/data/mysql` debido a la falta de espacio? Esto también se puede indicar por diversos síntomas, como interrupción del sitio, clientes que no pueden agregar productos al carro de compras, error de conexión a la base de datos y errores de Galería como _SQLSTATE\[08S01\]: error de vínculo de comunicación: 1047 WSREP_. Para obtener una lista de errores resultantes de un espacio en disco de [!DNL MySQL] bajo, consulte [[!DNL MySQL] espacio en disco bajo en Adobe Commerce en la infraestructura en la nube](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Si no está seguro de tener un problema de espacio en disco y tiene una cuenta de New Relic, vaya a la [página Hosts de supervisión de infraestructura de New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). A partir de ahí, haga clic en la ficha **Almacenamiento**, cambie el menú desplegable de **Gráfico que muestra** de 5 a 20 resultados y busque en la tabla el uso de disco alto en el gráfico o tabla % de disco usado. Para ver los pasos más detallados, consulte [Supervisión de infraestructura de New Relic > Pestaña Almacenamiento]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Si tiene alguno de los síntomas descritos anteriormente, compruebe el estado de sus inodes para asegurarse de que esto no esté siendo causado por un problema de número de archivo. Para ello, ejecute el siguiente comando en CLI/Terminal:\
`df -ih`

¿Es IUse% > 90%?

a. SÍ: esto se debe a que tiene demasiados archivos. Revise los pasos para quitar archivos de forma segura en [Eliminar archivos de forma segura cuando no haya espacio en disco, Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-26889). Continúe con [Paso 2](#step-2) después de completar estos pasos. Si desea solicitar más espacio, [envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Compruebe el espacio. Ejecute `df -h | grep mysql` y, a continuación, `df -h | grep tmp` en CLI/Terminal para comprobar el uso del espacio en disco en los directorios `/tmp` y `/data/mysql`. Continúe con [Paso 3](#step-3).

+++

## Paso 2: Comprobación del espacio en disco {#step-2}

+++**Comprobar el uso del espacio en disco?**

Una vez que haya reducido el número de archivos, ejecute `df -h | grep mysql` y luego `df -h | grep tmp` en la CLI/terminal para comprobar el uso del espacio en disco en `/tmp` y `/data/mysql`. ¿Se utiliza más del 70% para `/tmp` o `/data/mysql`?

a. SÍ - Continúe con [Paso 3](#step-3).
b. NO - Las consultas pueden estar agotando el almacenamiento disponible. Esto puede bloquear el nodo, desactivando la consulta y eliminando los `tmp` archivos. Examine el resultado de `SHOW PROCESSLIST;` en la CLI de [!DNL MySQL] en busca de consultas que puedan ser la causa del problema. [Envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando más espacio.

+++

## Paso 3: Identificar el directorio con un uso elevado {#step-3}

+++**¿Qué directorio ha usado más del 70%?**

¿Qué directorio utiliza más del 70 %? ¿`/tmp` o `/data/mysql`?

>[!NOTE]
>
>De forma predeterminada, el tmpdir de la base de datos escribe en `/tmp`. Para comprobar que la configuración de la base de datos sigue siendo la predeterminada, ejecute el siguiente comando en la CLI [!DNL MySQL]: `SHOW VARIABLES LIKE "TMPDIR";` Si el tmpdir de la base de datos sigue escribiendo en `/tmp`, verá `/tmp` en la columna Valor.

a. `/tmp` - Continúe con [Paso 4](#step-4). \
b. `/data/mysql` - Continúe con [Paso 5](#step-5).

+++

## Paso 4: Solución de problemas del montaje /tmp completo {#step-4}

+++**Solucionar problemas del montaje /tmp completo**

[Solucionar problemas del montaje /tmp completo para Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), desplácese hacia abajo por el artículo y pruebe las soluciones y prácticas recomendadas. A continuación, ejecute `df -h | grep mysql` y, a continuación, `df -h | grep tmp` en CLI/Terminal para comprobar el uso del espacio en disco en los directorios `/tmp` y `/data/mysql`\
  ¿Usado &lt; 70%?

>[!NOTE]
>
>Las soluciones de [Solucionar problemas de /tmp mount full para Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) están diseñadas para comerciantes que no han cambiado las variables de la base de datos tmpdir, que de forma predeterminada escribe en `/tmp`. Si ha cambiado el valor tmpdir, las instrucciones de [Solucionar problemas de /tmp mount full para Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) no le ayudarán.

a. SÍ - Ha resuelto el problema. \
b. NO - [Envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando más espacio.

+++

## Paso 5: Comprobación del valor predeterminado {#step-5}

+++**Comprobar predeterminado**

Es posible que la configuración de la base de datos ya no sea la predeterminada original. Busque la configuración tmpdir de la base de datos ejecutando en la CLI [!DNL MySQL]: `SELECT @@DATADIR;`. Si se genera `/data/mysql/`, el tmpdir de la base de datos está escribiendo en `/data/mysql/`. Intente aumentar el espacio en este directorio siguiendo los pasos indicados en [[!DNL MySQL] espacio en disco insuficiente en Adobe Commerce en nuestra infraestructura en la nube](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). A continuación, ejecute `df -h | grep mysql` y, a continuación, `df -h | grep tmp` en la CLI/terminal para comprobar el uso del espacio en disco en `/data/mysql` y `/tmp`.\
  ¿Usado &lt; 70%?

a. SÍ - Ha resuelto el problema. \
b. NO - [Envíe un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), solicitando más espacio.

+++

[Volver al paso 1](#step-1)

## Lectura relacionada

* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
