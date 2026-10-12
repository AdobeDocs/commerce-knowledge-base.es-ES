---
title: Cambiar la contraseña de administrador en Adobe Commerce en la infraestructura en la nube
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%
---
# Cambiar la contraseña de administrador en Adobe Commerce en la infraestructura en la nube

## Método 1: Olvidé su contraseña (restablecer por correo electrónico)

![login_panel_s.png](assets/login_panel_s.png)

Lea los pasos de la sección [Restablecer la contraseña del inicio de sesión de administrador](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in) en nuestra guía del usuario.

A continuación se muestran las notas de uso críticas.

### Habilitar correos electrónicos salientes

Antes de usar el formulario **Olvidé tu contraseña**, asegúrate de [habilitar los correos electrónicos salientes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html) mediante la [consola de Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html). Esto solo se aplica a los entornos de integración y a los proyectos de zonas protegidas.

Si los correos electrónicos salientes están verdaderamente desactivados en Pro Production o Staging, lo que significa que SendGrid no ha recogido el correo electrónico, puede comprobarlo marcando [Habilitar correos electrónicos en Cloud Console](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/outgoing-emails#enable-emails-in-the-cli). Si el problema persiste, puedes enviar un [ticket de soporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) de Adobe.

### Comprueba la carpeta Correo electrónico no deseado

Si no encuentra el mensaje con el vínculo Restablecer contraseña, compruebe la carpeta *Correo electrónico no deseado*. El nombre del correo electrónico es *Confirmación de restablecimiento de contraseña para el nombre de usuario del administrador*.

## Método 2: Añadir un nuevo usuario administrador

Si no puede restaurar o restablecer la contraseña del usuario existente, puede crear un nuevo usuario Administrador y establecer una contraseña para este usuario. Para ello, siga los siguientes pasos:

1. Use [SSH para iniciar sesión en el entorno remoto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Ejecute el siguiente comando: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
