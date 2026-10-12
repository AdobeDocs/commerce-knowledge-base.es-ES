---
title: Actualización del perfil de la cuenta en la nube
description: Este artículo proporciona los pasos para modificar el perfil en la cuenta de la nube de.
feature: Cloud, Support
role: Admin, Developer
exl-id: b0c9dbcf-9745-494d-a662-80c5c6378068
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 1%
---
# Actualización del perfil de la cuenta en la nube

Este artículo proporciona pasos sobre cómo modificar el perfil en la cuenta de la nube.

## Solución

Al modificar un perfil en la cuenta de la nube de, se pueden modificar los siguientes campos:

1. [!UICONTROL First name]
1. [!UICONTROL Last name]
1. [!UICONTROL Username]

   >[!NOTE]
   >
   >Al actualizar el nombre de usuario de Cloud Console, la dirección URL del proyecto cambia de `https://console.adobecommerce.com <old-username>/<project-id>` a `https://console.adobecommerce.com/<new-username>/<project-id>`.
   >
   >Después de la actualización, los vínculos que usan la dirección URL antigua ya no funcionarán. Los integrantes del equipo deben actualizar los marcadores guardados, la documentación interna y cualquier automatización para utilizar la nueva dirección URL.
   >
   >Este cambio solo se aplica a la nueva URL de la consola de Cloud. La dirección URL del proyecto heredado (`https://<region>.magento.cloud/projects/<project-id>`) no usa el nombre de usuario y continúa funcionando sin cambios.

Para modificar estos campos, siga estos pasos:

1. Ingresa a tu cuenta en [Adobe account login](https://accounts.magento.cloud).
1. Haga clic en la ficha **[!UICONTROL Account Settings]**.
1. Seleccione la casilla de verificación *crear nueva contraseña*.
1. Realice los cambios necesarios y haga clic en *guardar*.

>[!NOTE]
>
>Su contraseña no se cambiará.

## ¿Qué no se puede modificar?

1. **[!UICONTROL Password]**:
Para cambiar tu contraseña, visita [Adobe password reset](https://account.adobe.com/), ya que este perfil está enlazado a tu cuenta/dirección de correo electrónico allí.

1. **[!UICONTROL Email Address]**:
La modificación de este campo depende de las circunstancias individuales.

Si necesita transferir la propiedad de su cuenta actual a un nuevo propietario o a una dirección de correo electrónico diferente, deberá actualizar el correo electrónico del usuario principal asociado a la cuenta.

Consulte: [https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=en](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=en)
