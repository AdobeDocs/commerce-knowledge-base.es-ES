---
title: Problemas con los complementos del Compositor al actualizar a Adobe Commerce 2.4.4
description: Este artículo proporciona una solución para evitar el problema con los complementos del compositor al actualizar desde Adobe Commerce 2.4.3 y versiones anteriores a Adobe Commerce 2.4.4 o superiores (cuando se publiquen versiones futuras).
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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

1. Inicie la actualización como se describe en [Realización de una actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
1. Ejecute el `composer update` para actualizar la aplicación de Adobe Commerce.

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

A partir de julio de 2022, Composer cambiará el valor predeterminado de [`allow-plugins` opción](https://getcomposer.org/doc/06-config.md#allow-plugins) hasta `{}` Los complementos y ya no se cargarán a menos que se permitan.

## Solución

Añada lo siguiente a su `composer.json` , según cómo haya instalado Adobe Commerce:

* Si se ha creado el proyecto [uso del `composer create-project` mando](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html#get-the-metapackage):

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Si el proyecto se ha creado de otra manera y no tiene `"dealerdirect/phpcodesniffer-installer"` in `"require-dev"` sección:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

Después de actualizar el `composer.json` , ejecute el `composer update` y reinicie el proceso de actualización.
