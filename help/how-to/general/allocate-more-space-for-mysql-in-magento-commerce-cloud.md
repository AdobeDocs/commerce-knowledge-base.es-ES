---
title: Asigna más espacio para MySQL en Adobe Commerce en la nube
description: Este artículo contiene instrucciones sobre cómo asignar más espacio para MySQL en Adobe Commerce en la infraestructura en la nube.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Asigna más espacio para MySQL en Adobe Commerce en la nube


## Asignación de espacio en el plan inicial y la integración del plan profesional

Para todos los entornos del plan inicial y el plan profesional [Entorno de integración](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), puede asignar más espacio para MySQL en el `.magento/services.yaml` , aumentando el valor de `mysql: disk:` parámetro. Por ejemplo:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Consulte la [Configurar el servicio MySQL](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-mysql.html) artículo de referencia.

Una vez que haya cambiado la `.magento/services.yaml` , debe confirmar y enviar los cambios para que se apliquen. La notificación push almacenará en déclencheur el proceso de implementación.

>[!WARNING]
>
>Una partición de plan de inicio nunca debe hacerse más pequeña (por ejemplo, pasar de 30 GB a 20 GB) ya que esto probablemente resultará en una corrupción catastrófica de los datos.

## Asignar espacio en Ensayo o Producción de plan profesional

Para realizar estos cambios en el entorno de ensayo o producción del plan Pro, debe crear un [ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Al enviar un ticket de asistencia para aumentar el almacenamiento, el servicio de asistencia técnica deberá saber a qué partición y en qué cantidad se debe aplicar el almacenamiento (`/mysql` o `/exports`). Una solicitud de aumento de almacenamiento requiere la aprobación de su equipo de cuenta de Adobe, que revisará la cantidad de almacenamiento autorizada (según el formulario de pedido) antes de aprobarla.

## Reducir el espacio asignado no disponible (plan Pro y Starter)

El Soporte de Adobe Commerce puede hacer crecer una partición (`/mysql` o `/exports`), pero no puede reducir una partición. Existe el riesgo de que se dañen los datos al hacerlo, por lo que no está disponible la disminución del almacenamiento para una partición.
También es cierto para el plan de inicio, donde puede aumentar el espacio asignado usted mismo: no se recomienda reducir y podría provocar una corrupción catastrófica de los datos.
