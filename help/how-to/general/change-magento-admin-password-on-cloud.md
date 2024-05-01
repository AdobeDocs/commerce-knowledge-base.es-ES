---
title: Cambiar la contraseña de administrador en Adobe Commerce en la infraestructura en la nube
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 7dc84525aef4d59346bb9bc980a7ed9b7f6612cf
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Cambiar la contraseña de administrador en Adobe Commerce en la infraestructura en la nube

## Método 1: Olvidé su contraseña (restablecer por correo electrónico)

![login_panel_s.png](assets/login_panel_s.png)

Lea los pasos de la [Restablecer la sección de contraseña del inicio de sesión de administrador](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in) en nuestra guía del usuario.

A continuación se muestran las notas de uso críticas.

### Habilitar correos electrónicos salientes

Antes de usar el **Ha olvidado su contraseña** formulario, [habilitar correos electrónicos salientes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html) uso del [Consola de nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

### Comprueba la carpeta Correo electrónico no deseado

Si no encuentra el mensaje con el vínculo Restablecer contraseña, compruebe su *Correo electrónico no deseado* carpeta. El nombre del correo electrónico es *Confirmación de restablecimiento de contraseña para el nombre de usuario del administrador*.

## Método 2: Añadir un nuevo usuario administrador

Si no puede restaurar o restablecer la contraseña del usuario existente, puede crear un nuevo usuario Administrador y establecer una contraseña para este usuario. Para ello, siga los siguientes pasos:

1. Uso [SSH para iniciar sesión en el entorno remoto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Ejecute el siguiente comando: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
