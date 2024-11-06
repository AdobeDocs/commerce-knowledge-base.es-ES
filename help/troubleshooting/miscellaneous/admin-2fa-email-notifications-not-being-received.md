---
title: Administrador 2No se reciben notificaciones por correo electrónico de FA
description: Este artículo proporciona información sobre la resolución de problemas en los casos en los que no reciba el correo electrónico con las instrucciones de finalización de la configuración después de configurar la autenticación de doble factor (2FA) para mejorar la seguridad del acceso de administrador en Adobe Commerce en la infraestructura en la nube.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Administrador 2No se reciben notificaciones por correo electrónico de FA


## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, todas las versiones

## Problema

Ha configurado la autenticación de doble factor para mejorar la seguridad del acceso de administrador, pero no recibe el correo electrónico con las instrucciones para completar la configuración.

## Causa

Si no ha configurado correctamente el correo electrónico del remitente o si el dominio no se ha marcado como blanco en SendGrid, es probable que el correo electrónico haya terminado en la carpeta de correo no deseado.

## Resolución de problemas

### Paso 1: Comprobar la carpeta de correo no deseado

1. Si el correo electrónico no aparece en la carpeta de correo no deseado, ejecute esta consulta Mysql para comprobar que las direcciones de correo electrónico se han configurado:

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * Si no devuelve ningún resultado, significa que la dirección del remitente no se ha configurado.
Dado que no tiene acceso al administrador, deberá insertar la configuración en la base de datos. Conecte la dirección de correo electrónico adecuada y ejecute la instrucción MySQL:

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * Si devuelve un resultado, continúe con **Paso 2**.

1. Si el correo electrónico ha aparecido en su carpeta de correo no deseado, haga clic en el vínculo del mensaje. Si el vínculo ha caducado, intente iniciar sesión de nuevo para repetir el proceso.
1. Una vez que haya obtenido acceso, vaya a **Tiendas** > **Configuración** > **General** > **Almacenar direcciones de correo electrónico** y configure las direcciones de correo electrónico.

### Paso 2: Si/una vez que las direcciones de correo electrónico se han configurado correctamente, SSH en el entorno y ejecute este comando:

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Busque el correo electrónico en la carpeta de correo no deseado. Si el correo electrónico aparecía allí, [envía un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) para solicitar que el dominio se marque como blanco en SendGrid.

## Lectura relacionada

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) en nuestra documentación para desarrolladores.
