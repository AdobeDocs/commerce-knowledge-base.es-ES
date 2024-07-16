---
title: Bajo rendimiento en entornos de integración
description: Este artículo proporciona una solución para el problema en el que los entornos de integración Pro y los entornos de ensayo Starter tienen un rendimiento deficiente.
feature: Integration, Staging
role: Developer
source-git-commit: c0e2a8fdd2e4d231e56a3121544dbd8a25a8d60c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Bajo rendimiento en entornos de integración

Este artículo proporciona una solución para el problema en el que los entornos de integración Pro y los entornos de ensayo Starter tienen un rendimiento deficiente.

## Productos y versiones afectados:

* Adobe Commerce en la infraestructura en la nube (todas las versiones)

## Problema

Su entorno de integración Pro o entorno de ensayo Starter tiene un rendimiento deficiente.

## Causa

Según el tamaño del catálogo/datos o los requisitos de las integraciones/personalizaciones de terceros, es posible que se hayan superado los recursos disponibles en los entornos de integración.

## Solución

Para solucionar los problemas de rendimiento, asegúrese de seguir las prácticas recomendadas para obtener el mejor rendimiento en el entorno de integración. También es posible que deba solicitar una actualización de los entornos para mejorar la integración.

En primer lugar, determine si su entorno se encuentra en la [configuración de integración mejorada](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter).

* [Arquitectura profesional](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Arquitectura inicial](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Compruebe el registro de implementación mediante uno de estos métodos.

### Método 1:

Ejecute el siguiente comando mediante la CLI de nube:

`magento-cloud activity:log -e <branch name>`

### Método 2:

Compruebe el registro de implementación más reciente de ese entorno en [Cloud Console](https://console.adobecommerce.com).

Al final del registro de implementación, si ve algo como esto (la primera línea muestra el tamaño=XL y las líneas restantes muestran el tamaño=L), significa que se encuentra en la configuración de integración mejorada.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

Si no está en la configuración de la integración mejorada, puede [solicitar la mejora/actualización](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter).
Si ya está en la configuración de integración mejorada o sigue teniendo problemas de rendimiento después de la actualización, asegúrese de seguir las prácticas recomendadas para obtener un rendimiento óptimo en el entorno de integración:

* [Arquitectura profesional](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Arquitectura inicial](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Si ha cumplido las recomendaciones anteriores, [envíe una solicitud de soporte técnico](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) para obtener ayuda adicional.
 
