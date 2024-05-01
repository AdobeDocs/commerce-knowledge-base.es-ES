---
title: Ayuda general sobre solución de problemas del módulo personalizado
description: Este artículo habla sobre las herramientas generales para solucionar problemas de los módulos personalizados en Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Ayuda general sobre solución de problemas del módulo personalizado

Este artículo habla sobre las herramientas generales para solucionar problemas de los módulos personalizados en Adobe Commerce.

## Problema

Si se da cuenta de que hay un problema con las funciones del módulo personalizado y no recibe mensajes de error obvios que indiquen el problema, entonces querrá consultar los registros de su instancia.

## Solución

Compruebe los registros para ver si hay entradas con el nombre del módulo personalizado en el error.  En función de los errores implicados, la solución puede presentarse sola, o puede que necesite incluir la información de registro útil de Adobe Commerce si desea abrir un [Ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Consulte los siguientes párrafos para obtener información sobre la ubicación de los registros y las posibles soluciones.

### Adobe Commerce (todos los métodos de implementación), Magento Open Source, todas las versiones de 2.X

1. Ubicaciones de registros:
   * [Registros de arquitectura del plan inicial de Adobe Commerce en la infraestructura en la nube](/help/how-to/general/log-locations-directories-for-starter-plan.md) en nuestra base de conocimiento de soporte.
   * [registros de arquitectura de planificación de Adobe Commerce en la infraestructura en la nube Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) en nuestra base de conocimiento de soporte.
1. Según los errores que encuentre, si desea habilitar, deshabilitar o desinstalar un módulo personalizado, estos artículos detallan esas acciones:
   * [Habilitar o deshabilitar módulos](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html) en nuestra documentación para desarrolladores.
   * [Desinstalación de módulos](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html) en nuestra documentación para desarrolladores.

### Adobe Commerce en la infraestructura en la nube, todas las versiones

1. Ubicaciones de registros: [Adobe Commerce en registros de infraestructura en la nube](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) en nuestra documentación para desarrolladores.
1. Según los errores que encuentre, si desea habilitar, deshabilitar o desinstalar un módulo personalizado, estos artículos de la documentación para desarrolladores detallan esas acciones:
   * [Instalación, administración y actualización de extensiones](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html).
   * [Error de implementación de componente](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html).

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [Resumen del módulo](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Errores al instalar datos de ejemplo opcionales](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [Control de excepciones](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* [Excepciones durante la instalación](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [Ejecutar el Administrador de módulos](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [Archivos de configuración del módulo](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [Errores de falta de memoria](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
