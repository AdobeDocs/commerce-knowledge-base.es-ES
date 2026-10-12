---
title: 'Adobe Commerce cloud: el reíndice ha finalizado con el mensaje "Eliminado"'
description: '* Adobe Commerce en la infraestructura en la nube (todas las versiones)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%
---
# nube de Adobe Commerce: el reíndice ha finalizado con el mensaje `Killed`

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Problema

Está intentando ejecutar un reíndice en la rama de integración (o en Ensayo del proyecto de arquitectura inicial) y el proceso está finalizando con el mensaje `Killed`.

## Causa

Esto suele ocurrir porque los procesos de PHP se están quedando sin memoria.
El motivo más común es un gran número de productos, tiendas o grupos de clientes en la instancia.

## Solución

1. Reduzca el número de productos (así como los grupos de clientes y las tiendas, si corresponde).
1. Limite el uso a uno o dos usuarios simultáneos.
1. Deshabilite los trabajos cron y ejecute manualmente según sea necesario.
1. Si no se ha hecho anteriormente, solicite una actualización a los entornos de integración mejorada . Tome nota de la restricción en el número de entornos a los que estaría limitado una vez que se haya realizado la actualización. Consulte el artículo [Solicitud de mejora del entorno de integración - Pro y Starter](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242) en nuestra base de conocimiento de asistencia para obtener más información.

## Lectura relacionada:

En nuestra documentación para desarrolladores:

* [Arquitectura profesional > Entorno de integración](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Arquitectura de inicio > Entorno de ensayo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
