---
title: Durante la instalación, error de excepción de reflexión
description: Este artículo proporciona una solución para el error Excepción de reflexión durante la instalación.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Durante la instalación, error de excepción de reflexión

Este artículo proporciona una solución para el error Excepción de reflexión durante la instalación.

## Detalles {#details}

Durante la instalación, aparece un mensaje similar al siguiente:

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## Solución {#solution}

Borre todos los directorios y archivos del subdirectorio `var` de Adobe Commerce e instale de nuevo el software de Adobe Commerce.

Como [propietario del sistema de archivos de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) o como usuario con privilegios de `root`, introduzca los siguientes comandos:

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

Si utiliza Redis y sigue obteniendo un error, borre la caché de Redis de la siguiente manera:

```bash
$ redis-cli FLUSHALL
```
