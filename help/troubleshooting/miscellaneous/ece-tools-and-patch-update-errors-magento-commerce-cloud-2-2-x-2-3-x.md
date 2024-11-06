---
title: ECE-Tools y errores de actualización de parches Adobe Commerce cloud Infrastructure 2.2.x., 2.3.x
description: Este artículo proporciona una solución para el problema en el que se ven mensajes de error que incluyen "*failed to open stream:*" o "*No existe el archivo o directorio*" al intentar implementar actualizaciones en ECE-Tools, parches u otros cambios.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ECE-Tools y errores de actualización de parches Adobe Commerce cloud Infrastructure 2.2.x., 2.3.x

Este artículo proporciona una solución para el problema en el que se ven mensajes de error que incluyen &quot;*no se pudo abrir el flujo:*&quot; o &quot;*No existe ese archivo o directorio*&quot; al intentar implementar actualizaciones en ECE-Tools, parches u otros cambios.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube 2.2.x., 2.3.x

## Problema

Los errores al intentar implementar actualizaciones en ECE-Tools, parches u otros cambios incluyen: errores de PHP en la consola de Cloud y en `var/log/cloud.log`

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

Errores de registro de excepciones:

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## Causa

Configuración incorrecta del archivo `composer.json`.

## Solución

Si falta una configuración en el archivo `composer.json`, algunos directorios no se copiarán de la base de código de Adobe Commerce. El paquete y la actualización/parche no se pueden aplicar porque no se encontrarán los archivos.

Cambie la sección adicional para que coincida con la proporcionada a continuación y vuelva a intentar la implementación.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## Lectura relacionada

* [Actualizaciones y parches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/best-practices) en nuestra documentación para desarrolladores.
