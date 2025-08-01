---
title: Poco espacio en disco
description: Este artículo sugiere soluciones para la situación en la que se queda sin espacio en un entorno determinado de Adobe Commerce en la infraestructura en la nube.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Poco espacio en disco

Este artículo sugiere soluciones para la situación en la que se queda sin espacio en un entorno determinado de Adobe Commerce en la infraestructura en la nube.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura de la nube, todas [las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Se está quedando sin espacio en disco en el disco con directorios grabables. Un síntoma puede ser [implementación atascada](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-26878).

Para comprobar el uso del disco, ejecute el siguiente comando:

```bash
df -h var/
```

## Causa

El directorio `var` suele ser el que ocupa mucho espacio y se puede limpiar fácilmente.

Adobe Commerce almacena todos los archivos de registro en el directorio `var`. Se crean nuevos archivos de registro y se archivan los antiguos diariamente. Pero si el número de errores generados sigue aumentando, los archivos de registro ocupan cada vez más espacio.

Los archivos personalizados de importación y exportación también se almacenan en el directorio `var` y ocupan espacio si su número aumenta.

## Solución

Opciones de solución:

* Compruebe si tiene archivos de registro grandes e investigue por qué son grandes, corrija el problema y genere una gran cantidad de salida de registro.
* Limpie el directorio `var`.
* Configure un trabajo cron para rastrear el tamaño del directorio `var` y limpiarlo.
* Asigne más espacio en disco, si no lo ha utilizado. (Consulte la sección siguiente para obtener información sobre cómo comprobar cuál es su límite de espacio).
   * Para el plan inicial, todos los entornos y los entornos de integración del plan Pro, puede asignar el espacio en disco si no lo utiliza, como se describe en [Administrar espacio en disco: Asignación de espacio en disco](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space).
   * Para los entornos de ensayo y producción de planificación profesional, póngase en contacto con el servicio de asistencia para asignar más espacio en disco si tiene algún espacio sin utilizar.
* Si ha alcanzado el límite de espacio y sigue experimentando problemas de poco espacio, considere la posibilidad de comprar más espacio en disco, póngase en contacto con el equipo de cuenta de Adobe para obtener más información.

### Comprobar límite de espacio en disco

Para comprobar cuánto espacio tiene para cada Adobe Commerce en el entorno de la infraestructura en la nube:

1. Inicie sesión en [Cloud Console](https://console.adobecommerce.com).
1. En el panel **[!UICONTROL All projects]**, seleccione el proyecto correspondiente. En la esquina izquierda verá la disponibilidad de espacio en disco.

   ![espacio_de_proyecto.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
