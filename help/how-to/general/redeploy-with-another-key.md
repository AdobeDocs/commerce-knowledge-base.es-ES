---
title: 'Adobe Commerce en la nube: cambiar las claves de autenticación y volver a implementar'
description: Este artículo proporciona instrucciones sobre cómo volver a implementar Adobe Commerce en la infraestructura en la nube con claves de autenticación diferentes. Por ejemplo, es posible que haya utilizado las claves de otra cuenta o que haya utilizado claves Magento Open Source en lugar de claves Adobe Commerce.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%
---
# Adobe Commerce en la nube: cambiar las claves de autenticación y volver a implementar

Este artículo proporciona instrucciones sobre cómo volver a implementar Adobe Commerce en la infraestructura en la nube con claves de autenticación diferentes. Por ejemplo, es posible que haya utilizado las claves de otra cuenta o que haya utilizado claves Magento Open Source en lugar de claves Adobe Commerce.

Si utilizó las claves incorrectas, la implementación falla. Para recuperarse, debe clonar el proyecto, agregar las claves correctas a `auth.json` e insertar el cambio en la rama maestra.

En este artículo, suponemos que su proyecto tiene solamente una rama `master` (`master` es la rama predeterminada cuando crea un proyecto por primera vez).

Para volver a implementar con las claves de autenticación correctas:

1. Inicie sesión en el equipo que tenga las claves SSH de Adobe Commerce en la infraestructura de la nube.
1. Inicie sesión en el proyecto:

   ```
   magento-cloud login
   ```

1. Cree una rama para actualizar el código con el nombre `auth`:

   ```
   magento-cloud environment:branch auth master
   ```

1. Cambie al directorio raíz del proyecto.
1. Abra `auth.json` en un editor de texto.

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Añada las claves de autenticación correctas.
1. Guarde los cambios y salga del editor de texto.
1. Confirme y combine los cambios.

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. Espere a que se complete la implementación.

Los mensajes indican si la implementación se realizó correctamente. Para confirmar que la implementación se ha realizado correctamente, vaya a una de las **rutas del entorno** que se muestran en la pantalla.
