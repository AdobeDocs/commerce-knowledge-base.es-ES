---
title: Problemas de comprobación de preparación de permisos de archivos
description: 'Este artículo proporciona una corrección para los problemas de comprobación de preparación para permisos de archivos. El usuario del servidor web y el propietario del sistema de archivos de Adobe Commerce deben poder escribir en los directorios del sistema de archivos de Adobe Commerce, si corresponde. Si los permisos no están correctamente configurados, aparece un error similar al siguiente en el Asistente para configuración web:'
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Problemas de comprobación de preparación de permisos de archivos

Este artículo proporciona una corrección para los problemas de comprobación de preparación de permisos de archivos. El usuario del servidor web y el propietario del sistema de archivos de Adobe Commerce deben poder escribir en los directorios del sistema de archivos de Adobe Commerce, si corresponde. Si los permisos no están correctamente configurados, aparece un error similar al siguiente en el Asistente para configuración web:

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

La forma de resolver el problema depende de si tiene una configuración de un usuario o de dos:

* *Un usuario* significa que inicia sesión en el servidor de Adobe Commerce con el mismo usuario que también ejecuta el servidor web. Este tipo de configuración es común en entornos de alojamiento compartido.
* *Dos usuarios* significa que normalmente *no puede* inicie sesión como usuario del servidor web o cambie a él. Normalmente, se inicia sesión como un usuario y se ejecuta el servidor web como un usuario diferente. Esto es típico en el alojamiento privado o si tiene su propio servidor.

## Resolución de un usuario

Si tiene acceso desde la línea de comandos, escriba el siguiente comando suponiendo que Adobe Commerce esté instalado en `/var/www/html/magento2`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

Si no tiene acceso desde la línea de comandos, utilice un cliente FTP o una aplicación de administrador de archivos proporcionada por el proveedor de alojamiento para establecer permisos.

## Resolución para dos usuarios

Para introducir todos los comandos en una línea, introduzca lo siguiente suponiendo que Adobe Commerce está instalado en `/var/www/html/magento2` y el nombre del grupo de servidores web es `apache`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

En el sistema de archivos de evento, los permisos se establecen incorrectamente y el propietario del sistema de archivos de Adobe Commerce no los puede cambiar. Puede introducir el comando como usuario con `root` privilegios:

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
