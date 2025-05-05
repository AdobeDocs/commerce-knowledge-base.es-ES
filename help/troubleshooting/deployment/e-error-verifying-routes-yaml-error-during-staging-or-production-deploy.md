---
title: "E: Error al verificar el error routes.yaml durante la implementación de ensayo o producción"
description: 'Este artículo proporciona una solución para el problema de infraestructura de Adobe Commerce en la nube, donde aparece el mensaje de error *"E: Error while verifying routes.yaml"* al intentar implementar el proyecto en el entorno de ensayo o producción.'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E: Error al verificar el error routes.yaml durante la implementación de Ensayo o Producción

Este artículo proporciona una solución para el problema de infraestructura de Adobe Commerce en la nube, donde se obtiene el mensaje de error *&quot;E: Error while verifying routes.yaml&quot;* al intentar implementar el proyecto en el entorno de ensayo o producción.

## Versiones afectadas

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

<u>Pasos a seguir</u>:

Almacene en déclencheur una implementación insertando el código en el entorno de ensayo o producción.

<u>Comportamiento esperado</u>:

La implementación es correcta.

<u>Comportamiento real</u>:

La implementación se bloquea y se muestra el siguiente mensaje de error en el registro:

<pre>Implementar aplicaciones Comprobando configuración E: Error al verificar routes.yaml.
Los siguientes dominios están configurados para el clúster, pero no tienen rutas definidas en el archivo routes.yaml:

&#x200B;- store1.example.com
&#x200B;- store2.example.com
&#x200B;- test-store.example.com

Con su configuración actual de routes.yaml,
  no se proporcionarían estos dominios.

Para continuar, consulte aquí las instrucciones para solucionar los problemas:
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## Causa

Este error se produce si falta la configuración de ruta de cualquier dominio adicional agregado al proyecto en el archivo `routes.yaml`.

Como parte de la actualización de la habilitación de autoservicio de Adobe Commerce para la configuración de rutas de autoservicio, hemos agregado una comprobación previa a la implementación para garantizar que todos los dominios del proyecto tengan rutas configuradas en el archivo `routes.yaml`. Si a algún dominio le falta la configuración de ruta, la implementación se bloquea.

## Solución

Para resolver la implementación bloqueada, actualice el archivo `routes.yaml` para configurar las rutas de los dominios enumerados en el mensaje de error mediante cualquiera de los métodos siguientes:

* Aplique el parche proporcionado por Adobe Commerce durante el proceso de actualización.
* Agregue manualmente la configuración de ruta que falta al archivo `routes.yaml`.

### Método 1: Aplicar el parche proporcionado por Adobe Commerce

1. Busque un vale de soporte de Adobe Commerce reciente con el título &quot;*Habilitar características de autoservicio para &lt;project\_ID>&quot;.*
1. Siga las instrucciones del ticket para aplicar el parche, que actualiza la configuración de ruta para su entorno de nube.
1. СConfirme y envíe los cambios para volver a implementar el proyecto.

### Método 2: agregar manualmente la configuración de ruta que falta

1. Para servir todos los dominios del proyecto utilizando la misma configuración de ruta, actualice el archivo `routes.yaml` agregando plantillas de ruta para el dominio predeterminado y todos los demás dominios del proyecto, como se muestra en el ejemplo siguiente:

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. СConfirme y envíe los cambios para volver a implementar el proyecto.

Para obtener instrucciones detalladas sobre cómo actualizar la configuración de la ruta, consulta [Cloud for Adobe Commerce > Configure routes](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml) en nuestra documentación para desarrolladores.

>[!NOTE]
>
>Si la configuración del proyecto especifica dominios que ya no están en uso, complete los siguientes pasos para eliminarlos del proyecto lo antes posible: 1. Envíe un ticket de asistencia técnica con una lista de dominios para eliminar de los entornos de proyecto. 2. Una vez que el equipo de soporte técnico elimine los dominios, actualice el archivo `routes.yaml` para quitar las referencias a los dominios obsoletos.
