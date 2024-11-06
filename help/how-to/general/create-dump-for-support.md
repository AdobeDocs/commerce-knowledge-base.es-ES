---
title: Cómo crear un volcado "borrado" cuando lo solicita el agente de soporte
description: Este artículo proporciona información sobre cómo crear un volcado "depurado" (copia de seguridad) de la base de datos y código del administrador de Adobe Commerce cuando un agente de soporte de Adobe Commerce lo solicita para proporcionar uno. Este volcado excluye los archivos multimedia para acelerar el proceso y generar un archivo mucho más pequeño. Todos los datos confidenciales se colocan en un hash al realizar la copia de seguridad de la base de datos.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Cómo crear un volcado &quot;borrado&quot; cuando lo solicita el agente de soporte


## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.3.x, 2.4.x.

## Crear un volcado &quot;borrado&quot;

Cree un volcado &quot;borrado&quot; desde Admin:

1. En el Administrador de Commerce, vaya a **Sistema** > **Soporte técnico** > **Recopilador de datos**.
1. Haga clic en **Nueva copia de seguridad**.
1. Después de unos minutos, haz clic en **Actualizar estado** (puede tardar más, repite cada 5 minutos hasta que se complete).
1. Reubique los archivos de volcado generados del directorio `/var/support` al directorio raíz de Adobe Commerce.

A continuación, puede proporcionar al Soporte técnico el vínculo de descarga directa a los archivos de volcado (la dirección de almacenamiento y el nombre de archivo tal y como se muestra).

Si tiene problemas al crear volcados desde el administrador, considere la posibilidad de utilizar comandos CLI como se describe en [Ejecute las utilidades de asistencia](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/run-support-utilities) en nuestra documentación para desarrolladores.

## Lectura relacionada

* [Cree una copia de seguridad completa de la base de datos para Adobe Commerce en la infraestructura en la nube](/help/how-to/general/create-database-dump-on-cloud.md) en nuestra base de conocimiento de asistencia.
