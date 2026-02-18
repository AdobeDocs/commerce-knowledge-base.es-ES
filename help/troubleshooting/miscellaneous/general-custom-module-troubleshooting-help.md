---
title: Ayuda general sobre solución de problemas del módulo personalizado
description: Este artículo habla sobre las herramientas generales para solucionar problemas de los módulos personalizados en Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Ayuda general sobre solución de problemas del módulo personalizado

Este artículo habla sobre las herramientas generales para solucionar problemas de los módulos personalizados en Adobe Commerce.

## Problema

Si se da cuenta de que hay un problema con las funciones del módulo personalizado y no recibe mensajes de error obvios que indiquen el problema, entonces querrá consultar los registros de su instancia.

## Solución

Compruebe los registros para ver si hay entradas con el nombre del módulo personalizado en el error.  En función de los errores involucrados, la solución puede presentarse por sí misma, o puede que necesite incluir su información de registro útil de Adobe Commerce si desea abrir un [ticket de asistencia](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket). Consulte los siguientes párrafos para obtener información sobre la ubicación de los registros y las posibles soluciones.

### Adobe Commerce (todos los métodos de implementación), Magento Open Source, todas las versiones 2.X

1. La ubicación de los registros se ubica en [Adobe Commerce en la infraestructura en la nube, registros de arquitectura de plan Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) en nuestra base de conocimiento de soporte.
1. Según los errores que encuentre, si desea habilitar, deshabilitar o desinstalar un módulo personalizado, estos artículos detallan esas acciones:
   * [Habilite o deshabilite módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/manage-modules) en nuestra documentación para desarrolladores.
   * [Desinstalar módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) en nuestra documentación para desarrolladores.

### Adobe Commerce en la infraestructura en la nube, todas las versiones

1. Ubicaciones de registros: [Adobe Commerce en registros de infraestructura en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) en nuestra documentación para desarrolladores.
1. Según los errores que encuentre, si desea habilitar, deshabilitar o desinstalar un módulo personalizado, estos artículos de la documentación para desarrolladores detallan esas acciones:
   * [Instalar, administrar y actualizar extensiones](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).
   * [Error de implementación de componente](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment).

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [Resumen del módulo](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [Errores al instalar datos de ejemplo opcionales](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/errors-installing-optional-sample-data)
* [Control de excepciones](https://developer.adobe.com/commerce/webapi/graphql/develop/exceptions/)
* [Excepciones durante la instalación](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/exceptions-during-installation)
* [Ejecutar el Administrador de módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites)
* [Archivos de configuración de módulo](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)
* [Errores de memoria insuficiente](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)
