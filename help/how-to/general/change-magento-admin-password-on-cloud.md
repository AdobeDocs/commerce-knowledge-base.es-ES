---
title: Cambiar la contraseña de administrador en Adobe Commerce en la infraestructura en la nube
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 44238f6d57458028cb1e2612d45e1e12b3f39916
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Cambiar la contraseña de administrador en Adobe Commerce en la infraestructura en la nube

## Método 1: Olvidé su contraseña (restablecer por correo electrónico)

![login_panel_s.png](assets/login_panel_s.png)

Lea los pasos de la sección [Restablecer la contraseña del inicio de sesión de administrador](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html?lang=es#admin-sign-in) en nuestra guía del usuario.

A continuación se muestran las notas de uso críticas.

### Habilitar correos electrónicos salientes

Antes de usar el formulario **Olvidé tu contraseña**, asegúrate de [habilitar los correos electrónicos salientes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html?lang=es) mediante la [consola de Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=es). Esto solo se aplica a los entornos de integración y a los proyectos de zonas protegidas.

Si los correos electrónicos salientes están verdaderamente desactivados en Pro Production o Staging, lo que significa que SendGrid no ha recogido el correo electrónico, puede comprobarlo marcando [Habilitar correos electrónicos en Cloud Console](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/project/outgoing-emails#enable-emails-in-the-cli). Si el problema persiste, puedes enviar un [ticket de soporte](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) de Adobe.

### Comprueba la carpeta Correo electrónico no deseado

Si no encuentra el mensaje con el vínculo Restablecer contraseña, compruebe la carpeta *Correo electrónico no deseado*. El nombre del correo electrónico es *Confirmación de restablecimiento de contraseña para el nombre de usuario del administrador*.

## Método 2: Añadir un nuevo usuario administrador

Si no puede restaurar o restablecer la contraseña del usuario existente, puede crear un nuevo usuario Administrador y establecer una contraseña para este usuario. Para ello, siga los siguientes pasos:

1. Use [SSH para iniciar sesión en el entorno remoto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=es).
1. Ejecute el siguiente comando: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
