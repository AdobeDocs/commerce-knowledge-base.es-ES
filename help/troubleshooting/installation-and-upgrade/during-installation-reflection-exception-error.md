---
title: Durante la instalación, error de excepción de reflexión
description: Este artículo proporciona una solución para el error Excepción de reflexión durante la instalación.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '107'
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
