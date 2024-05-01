---
title: La descarga falla debido a cambios en el Compositor
description: Este artículo proporciona una corrección para un error de descarga y excepción de Adobe Commerce.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# La descarga falla debido a cambios en el Compositor

Este artículo proporciona una corrección para un error de descarga y excepción de Adobe Commerce.

## Problema

Durante la descarga, se muestra el siguiente error:

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Causa

Esto sucede debido a cambios en ciertas versiones de Composer. La solución consiste en reducir Composer a una versión anterior e intentar descargar Adobe Commerce de nuevo.

## Solución

Cualquier versión de Composer fechada entre el 21 de noviembre y el 26 de noviembre de 2015 tiene este problema. Para confirmar que este problema está relacionado con la versión de Composer, introduzca el siguiente comando:

```php
composer -v
```

La versión se muestra de forma similar a la siguiente:

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

Tenga en cuenta que la fecha es 2015-11-25, lo que indica que Composer tiene este problema.

Para solucionarlo:

1. Cambie la versión de Composer para poder descargar el software de Adobe Commerce mediante cualquiera de estas acciones:

   * Degradar Composer con el siguiente comando: `composer self-update 1.0.0-alpha11`.
   * Actualice Composer a una versión posterior al 26 de noviembre de 2015: `composer self-update`.

1. Elimine el directorio y los subdirectorios de Adobe Commerce.
1. Vuelva a intentar la descarga mediante uno de estos métodos `[composer create-project](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html)` o `[git clone](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/dev_install.html)`.
1. Después de descargar correctamente el software de Adobe Commerce, actualice Compositor: `composer self-update`.
