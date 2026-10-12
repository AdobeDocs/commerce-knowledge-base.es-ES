---
title: No se puede acceder a Adobe Commerce en la IU de infraestructura de nube
description: Este artículo proporciona soluciones para el problema en el que no puede iniciar sesión en la interfaz de usuario de Adobe Commerce en la infraestructura de la nube y obtener el "error 403".
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
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
source-wordcount: '332'
ht-degree: 0%
---
# No se puede acceder a Adobe Commerce en la IU de infraestructura de nube

Este artículo proporciona soluciones para el problema que impide iniciar sesión en Adobe Commerce en la interfaz de usuario de la infraestructura en la nube y obtener el *error 403*.

## Problema

Al intentar iniciar sesión en la interfaz de usuario de Adobe Commerce en la nube por primera vez, aparece el error *403: Acceso al entorno denegado*. Este error puede deberse a que se carga la rama maestra en la dirección URL de la nube por primera vez y es posible que no tenga acceso a esa rama.

## Solución

Si aparece un error 403 al acceder a la dirección URL por primera vez, asegúrese de que tiene una función en la rama maestra.

1. СPóngase en contacto con el propietario de la licencia o con un superusuario del proyecto y asegúrese de que le hayan proporcionado acceso como **usuario de nivel de entorno**, tal y como se describe en [Proyectos en la nube > Administrar usuarios desde la consola en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console) en nuestra documentación para desarrolladores.

   Si solo tiene una función aplicable en una rama específica, debe ir a la dirección URL de esa rama, por ejemplo,
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   La próxima vez que acceda a la dirección URL principal, se seleccionará de forma predeterminada el último entorno que haya visitado.

1. Si sigue sin poder iniciar sesión, сpóngase en contacto con el propietario de la licencia o con un superusuario del proyecto y asegúrese de que le hayan proporcionado acceso como **usuario de nivel de proyecto**, tal como se describe en [Proyectos en la nube > Agregar un usuario al proyecto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project) en nuestra documentación para desarrolladores.
1. Si el error persiste, [envíe un ticket de asistencia](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
