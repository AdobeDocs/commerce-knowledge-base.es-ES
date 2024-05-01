---
title: "Adobe Commerce en la nube: cambiar las claves de autenticación y volver a implementar"
description: Este artículo proporciona instrucciones sobre cómo volver a implementar Adobe Commerce en la infraestructura en la nube con claves de autenticación diferentes. Por ejemplo, es posible que haya utilizado las claves de otra cuenta o que haya utilizado claves de Magento Open Source en lugar de claves de Adobe Commerce.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce en la nube: cambiar las claves de autenticación y volver a implementar

Este artículo proporciona instrucciones sobre cómo volver a implementar Adobe Commerce en la infraestructura en la nube con claves de autenticación diferentes. Por ejemplo, es posible que haya utilizado las claves de otra cuenta o que haya utilizado claves de Magento Open Source en lugar de claves de Adobe Commerce.

Si utilizó las claves incorrectas, la implementación falla. Para recuperarse, debe clonar el proyecto y añadir las claves correctas a `auth.json`y presione el cambio en la rama maestra.

En este artículo, suponemos que su proyecto tiene un `master` solo rama (`master` es la rama predeterminada cuando se crea un proyecto por primera vez).

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
1. Abrir `auth.json` en un editor de texto.

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

Los mensajes indican si la implementación se realizó correctamente. Para confirmar que la implementación se ha realizado correctamente, vaya a uno de los **Rutas de entorno** se muestra en la pantalla.
