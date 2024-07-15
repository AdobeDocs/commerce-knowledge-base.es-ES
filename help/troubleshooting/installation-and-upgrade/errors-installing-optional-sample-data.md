---
title: Errores al instalar datos de ejemplo opcionales
description: En este tema se tratan las soluciones a los errores que pueden producirse al instalar datos de ejemplo opcionales.
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Errores al instalar datos de ejemplo opcionales

En este tema se tratan las soluciones a los errores que pueden producirse al instalar datos de ejemplo opcionales.

## Síntoma (permisos del sistema de archivos)

Error en el registro de la consola durante la instalación de datos de ejemplo mediante el Asistente para la instalación:

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

Estas excepciones son el resultado de la configuración de permisos del sistema de archivos.

### Solución

[Vuelva a establecer la propiedad y los permisos del sistema de archivos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) como usuario con privilegios de `root`.

## Síntoma (modo de producción)

Si actualmente está configurado para [modo de producción](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html), la instalación de datos de ejemplo falla si usa el comando [magento sampledata:deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html):

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### Solución

No instale datos de ejemplo en el modo de producción. Cambie al modo de desarrollador y borre algunos `var` directorios e inténtelo de nuevo.

Escriba los siguientes comandos en el orden mostrado como [propietario del sistema de archivos de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html):

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## Síntoma (seguridad)

Durante la instalación de datos de ejemplo opcionales, aparece un mensaje similar al siguiente:

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### Solución

Durante la instalación de datos de ejemplo, deshabilite SELinux con un recurso como:

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [Documentación de CentOS](https://docs.centos.org/en-US/docs/)

## Síntoma (desarrollar rama)

Se muestran otros errores, como:

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### Solución

Hay problemas conocidos con el uso de datos de ejemplo con la rama de desarrollo de Adobe Commerce. En su lugar, utilice la rama maestra. Puede cambiar a la rama maestra de la siguiente manera:

```php
cd <magento_root>
git checkout master
git pull origin master
```

## Síntoma (max_execution_time)

La instalación se detiene antes de que finalice la instalación de los datos de ejemplo. A continuación se muestra un ejemplo:

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

La instalación de los datos de ejemplo no finaliza.

Este error se produce cuando se supera el tiempo de ejecución máximo configurado para los scripts PHP. Como la carga de datos de ejemplo puede llevar mucho tiempo, puede aumentar el valor durante la instalación.

### Solución

Como usuario con privilegios de `root`, modifique `php.ini` para aumentar el valor de `max_execution_time` a 600 o más. (600 segundos son 10 minutos. Puede aumentar el valor a lo que desee). Debe volver a cambiar `max_execution_time` a su valor anterior una vez completada la instalación.

Si no está seguro de dónde se encuentra `php.ini`, escriba el siguiente comando:

```php
php --ini
```

El valor de `Loaded Configuration File` es el `php.ini` que debe modificar.

>[!NOTE]
>
>Somos conscientes de que este artículo aún puede contener términos de software estándar en la industria que algunos pueden encontrar racistas, sexistas u opresivos y que pueden hacer que el lector se sienta herido, traumatizado o no deseado. El Adobe de está trabajando para eliminar estos términos de nuestro código, documentación y experiencias de usuario.
