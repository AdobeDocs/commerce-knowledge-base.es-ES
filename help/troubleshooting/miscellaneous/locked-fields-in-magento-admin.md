---
title: Campos bloqueados en el administrador de Commerce
description: Este artículo proporciona una solución para los casos en los que no se pueden modificar campos en el Administrador de Commerce.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Campos bloqueados en el administrador de Commerce

Este artículo proporciona una solución para los casos en los que no se pueden modificar campos en el Administrador de Commerce.

## Productos y versiones afectados

* Adobe Commerce local 2.3.x, 2.4.x
* Adobe Commerce en cloud Infrastructure 2.3.x, 2.4.x

## Problema

Una vez guardado un cambio en la configuración de en `app/etc/env.php` o `app/etc/config.php`, no puede modificar la configuración en el Administrador.

<u>Pasos a seguir</u>:

Nota: Este es un ejemplo: el problema puede afectar a todas las configuraciones que se han guardado.

1. El comerciante guarda las credenciales de sus métodos de entrega mediante el siguiente comando en el terminal: `./vendor/bin/ece-tools config:dump`. Esto guarda las credenciales en la `app/etc/env.php` archivo.
1. A continuación, el comerciante intenta cambiar las credenciales más adelante.

<u>Resultados esperados</u>:

El comerciante puede establecer los valores en la configuración del campo Administración y guardarlos.

<u>Resultados reales</u>:

Los campos del Administrador están bloqueados o los valores se pueden cambiar, pero no se guardarán en el Administrador.

## Causa

Cuando la configuración se guarde en `env.php` o `config.php`, no podrá modificar la configuración en el Administrador. Para permitir la edición de la configuración, deberá quitar la configuración de `env.php` o `config.php`.

## Solución

Asegúrese de que la configuración de no se ha guardado en `app/etc/env.php` o `app/etc/config.php`. Si se ha guardado, intente los siguientes pasos:

* `config.php` - Quite la configuración y vuelva a implementar.
* `env.php` - Modifique esto directamente en el servidor y quite la configuración, luego ejecute `bin/magento app:config:import`.

## Lectura relacionada

* [Exportar la configuración](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-export.html#sensitive-or-system-specific-settings) en nuestra documentación para desarrolladores.
* [Establecer valores de configuración](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-set.html#config-cli-config-set) en nuestra documentación para desarrolladores.
* [Adobe Commerce en la infraestructura en la nube: reduzca el tiempo de inactividad de la implementación con Configuration Management](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) en nuestra base de conocimiento de soporte.
