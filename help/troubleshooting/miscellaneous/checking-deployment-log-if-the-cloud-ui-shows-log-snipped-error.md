---
title: Comprobación del registro de implementación si la IU de Cloud tiene el error "registro recortado"
description: Este artículo proporciona una solución para el problema en el que la interfaz de usuario de Adobe Commerce en la infraestructura en la nube muestra el mensaje de error *log snipped porque era demasiado largo* al intentar ver el registro de implementación en la interfaz de usuario del proyecto en la nube.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%
---
# Comprobando el registro de implementación si la IU de la nube tiene *error de registro recortado*

Este artículo proporciona una solución para el problema en el que Adobe Commerce en la interfaz de usuario de la infraestructura en la nube muestra el *registro recortado porque era demasiado largo* mensaje de error al intentar ver el registro de implementación en la interfaz de usuario del proyecto en la nube. (No se aplica a [Adobe Commerce Cloud Console](https://console.adobecommerce.com/)).

## Productos afectados

Adobe Commerce en la infraestructura en la nube (todas las versiones compatibles)

## Problema

Al intentar ver el registro de implementación en la interfaz de usuario del proyecto en la nube, Adobe Commerce en la interfaz de usuario de la infraestructura en la nube muestra el siguiente mensaje de error: *registro recortado porque era demasiado largo*.

## Pasos a seguir

1. Vaya a la dirección URL del proyecto y haga clic en el **Estado** de la implementación en cuestión.
1. Si el registro es demasiado largo para mostrarlo en la interfaz de usuario, se mostrará el mensaje de error: *registro recortado porque es demasiado largo*.

## Causa

Tenga en cuenta que el registro que se muestra en la interfaz de usuario no debe tratarse como la fuente fiable, especialmente si descubre que el sitio no responde o no funciona correctamente después de que la implementación se haya enumerado con un estado de éxito. También debe comprobarlo con los registros del servidor. Consulte [Ver y administrar registros](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=es) en nuestra documentación para desarrolladores.

## Solución

1. Asegúrese de que tiene [Magento Cloud CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=es) instalado en su entorno local.
1. Puede ejecutar cualquiera de los siguientes comandos:

   ```bash
   magento-cloud act -p <project id> -e <environment>
   ```

   ```bash
   magento-cloud activity:list -p <project id> -e <environment>
   ```

1. Devolverán un resultado similar al siguiente:

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. Copie el ID de actividad de la implementación afectada y, a continuación, ejecute el comando:

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   Ejemplo para examinar el registro de la implementación fallida:

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## Lecturas relacionadas en nuestra documentación para desarrolladores:

* [Adobe Commerce en la infraestructura en la nube > Creación e implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=es)
* [Adobe Commerce en la infraestructura de la nube > Ver y administrar registros](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=es)
