---
title: Error "La versión actual de RDBMS no es compatible" en la implementación
description: 'Este artículo proporciona una solución para los casos en los que una implementación falla y tiene el siguiente error en el registro de implementación: *la versión actual de RDBMS no es compatible*.'
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%
---
# Error &quot;La versión actual de RDBMS no es compatible&quot; en la implementación

Este artículo proporciona una solución para los casos en los que una implementación falla y tiene el siguiente error en el registro de implementación: *no se admite la versión actual de RDBMS*.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Problema

Este mensaje de error significa que la versión actual de MariaDB ya no es compatible con la versión de Adobe Commerce a la que intenta actualizar y MariaDB debe actualizarse a una versión compatible.


<u>Pasos a seguir</u>:

Intento de implementación.

<u>Resultado esperado</u>:

Implementación correcta.

<u>Resultado real</u>:

La implementación falla con un mensaje de error: *no se admite la versión actual de RDBMS*.

## Causa

Su versión de MariaDB no es compatible con la versión de Adobe Commerce a la que intenta actualizar.

## Solución

Debe actualizar el servicio MariaDB a una versión compatible antes de actualizar la aplicación.


Para la rama de integración en la arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube (y todas las ramas en la arquitectura de inicio), siga [Configurar servicio](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/service/services-yaml) en nuestra documentación para desarrolladores.

Para la arquitectura del plan Pro de ensayo y producción en Adobe Commerce en la infraestructura en la nube, [envíe un vale de soporte](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) para solicitar que los servicios se actualicen antes de implementar la actualización de la versión de Adobe Commerce.


## Lectura relacionada

* [Prácticas recomendadas para compilaciones e implementación](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) en nuestra documentación para desarrolladores.
* [Actualización a Adobe Commerce 2.3.5: tablas compactas a dinámicas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=es) en nuestra base de conocimientos de soporte.
