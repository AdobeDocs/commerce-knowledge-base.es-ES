---
title: La implementación se bloqueó con el error "No se puede cargar la aplicación en el clúster remoto"
description: 'Este artículo proporciona una solución para el problema de Adobe Commerce, donde la implementación se bloquea y el siguiente mensaje de error se puede encontrar en el registro de implementación: *"Error: No se puede cargar la aplicación en el clúster remoto"*.'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# La implementación se bloqueó con el error &quot;No se puede cargar la aplicación en el clúster remoto&quot;

Este artículo proporciona una solución para el problema de Adobe Commerce, donde la implementación se bloquea y el siguiente mensaje de error se puede encontrar en el registro de implementación: *&quot;Error: no se puede cargar la aplicación en el clúster remoto&quot;*.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

<u>Pasos a seguir</u>:

Déclencheur la implementación manualmente o realizando una combinación, inserción o sincronización de su entorno.

<u>Resultado esperado</u>:

La implementación se ha completado correctamente.

<u>Resultado real</u>:

La implementación se atasca y aparece el siguiente mensaje de error en el registro de errores de implementación de la interfaz de usuario de la nube: *&quot;Error: no se puede cargar la aplicación en el clúster remoto&quot; encontrado en el registro de implementación después de una implementación fallida, el sitio puede mostrar el error &quot;Tiempo de espera de primer byte 503&quot;*.

## Causa

El problema se debe a la interrupción del almacenamiento disponible.

## Solución

Puede considerar la posibilidad de limpiar los directorios de registro o aumentar el espacio en disco.

Directorios que se deben considerar para la limpieza:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Para obtener más información sobre cómo aumentar el espacio en disco si utiliza la arquitectura del plan de inicio de la infraestructura en la nube de Adobe Commerce, consulte [Aumente el espacio en disco para el entorno de integración en la nube](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md) en nuestra base de conocimiento de soporte. Las mismas instrucciones se pueden utilizar para aumentar el espacio del entorno de integración de arquitectura de plan Pro de Adobe Commerce en la infraestructura en la nube. Para Producción/ensayo profesional, debe hacer lo siguiente [presentar un ticket al Soporte de Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) y solicitar más espacio en disco. Pero, por lo general, no tendrá que lidiar con esto en el plan de ensayo/producción de Pro, ya que Adobe Commerce monitoriza estos parámetros por usted y alerta y/o toma acciones según el contrato.
