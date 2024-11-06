---
title: Error "La versión actual de RDBMS no es compatible" en la implementación
description: "Este artículo proporciona una solución para los casos en los que una implementación falla y tiene el siguiente error en el registro de implementación: *la versión actual de RDBMS no es compatible*."
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '272'
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


Para la rama de integración en la arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube (y todas las ramas en la arquitectura de inicio), siga [Configurar servicio](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml) en nuestra documentación para desarrolladores.

Para la arquitectura del plan Pro de ensayo y producción en Adobe Commerce en la infraestructura en la nube, [envíe un vale de soporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar que los servicios se actualicen antes de implementar la actualización de la versión de Adobe Commerce.


## Lectura relacionada

* [Prácticas recomendadas para compilaciones e implementación](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) en nuestra documentación para desarrolladores.
* [Actualización a Adobe Commerce 2.3.5: tablas compactas a dinámicas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) en nuestra base de conocimientos de soporte.
