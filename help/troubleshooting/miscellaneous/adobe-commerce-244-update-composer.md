---
title: Problemas con los complementos del Compositor al actualizar a Adobe Commerce 2.4.4
description: Este artículo proporciona una solución para evitar el problema con los complementos del compositor al actualizar desde Adobe Commerce 2.4.3 y versiones anteriores a Adobe Commerce 2.4.4 o superiores (cuando se publiquen versiones futuras).
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Problemas con los complementos del Compositor al actualizar a Adobe Commerce 2.4.4

Este artículo proporciona una solución para evitar problemas con los complementos del compositor al actualizar desde Adobe Commerce 2.4.3 y versiones anteriores a Adobe Commerce 2.4.4 o superiores (cuando se publiquen versiones futuras).

## Productos y versiones afectados

* Adobe Commerce local, cualquier versión al actualizar a 2.4.4 o superior (cuando esté disponible)
* Adobe Commerce en la infraestructura en la nube, cualquier versión al actualizar a 2.4.4 o superior (cuando esté disponible)
* Magento Open Source, cualquier versión al actualizar a 2.4.4 o superior (cuando esté disponible)

## Problema

Al actualizar a Adobe Commerce 2.4.4 o superior después de julio de 2022, es posible que Composer le avise sobre los complementos.

<u>Pasos a seguir</u>:

Requisitos previos: Adobe Commerce 2.4.3 o anterior está instalado.

1. Inicie la actualización tal como se describe en [Realizar una actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
1. Ejecute el comando `composer update` para actualizar la aplicación de Adobe Commerce.

<u>Resultados esperados</u>:

La actualización se ha realizado correctamente.

<u>Resultados reales</u>:

La instalación falla con un error similar al siguiente:

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Causa

A partir de julio de 2022, el Compositor cambia el valor predeterminado de la opción [`allow-plugins` ](https://getcomposer.org/doc/06-config.md#allow-plugins) a `{}` y los complementos ya no se cargarán a menos que se permita.

## Solución

Agregue lo siguiente al archivo `composer.json`, según la instalación de Adobe Commerce:

* Si el proyecto se ha creado [con el comando `composer create-project`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer#get-the-metapackage):

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Si el proyecto se creó de otra manera y no tiene `"dealerdirect/phpcodesniffer-installer"` en la sección `"require-dev"`:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

Después de actualizar el archivo `composer.json`, ejecute el comando `composer update` y reinicie el proceso de actualización.
