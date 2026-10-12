---
title: Error de lista de deseos durante la actualización a las versiones de Adobe Commerce 2.3.4-p1 o 2.3.5
description: Este artículo proporciona una corrección del problema conocido al actualizar a las versiones de Adobe Commerce 2.3.4-p1 y 2.3.5 relacionado con un error de la lista de deseos durante la actualización a estas versiones.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
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
source-wordcount: '388'
ht-degree: 0%
---
# Error de lista de deseos durante la actualización a las versiones de Adobe Commerce 2.3.4-p1 o 2.3.5

Este artículo proporciona una corrección del problema conocido al actualizar a las versiones de Adobe Commerce 2.3.4-p1 y 2.3.5 relacionado con un error de la lista de deseos durante la actualización a estas versiones.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.3.4-p1 y 2.3.5
* Adobe Commerce local 2.3.4-p1 y 2.3.5

## Problema

Al actualizar Adobe Commerce (todos los métodos de implementación) y Magento Open Source a la versión 2.3.5 o 2.3.4-p1, puede obtener un error de lista de deseos (detallado a continuación) del módulo:

```php
Magento_Wishlist
```

La actualización de Adobe Commerce (todos los métodos de implementación)/Magneto Open Source versión 2.3.4-p1 **a la versión 2.3.4-p2** o de Adobe Commerce (todos los métodos de implementación)/Magneto Open Source versión 2.3.5 **a la versión 2.3.5-p1** corregirá el error.

<u>Pasos a seguir</u>:

Actualice Adobe Commerce (todos los métodos de implementación)/Magento Open Source a la versión 2.3.4-p1 o 2.3.5.

<u>Resultado esperado</u>:

El proceso de actualización a Adobe Commerce (todos los métodos de implementación)/Magento Open Source versión 2.3.4-p1 o 2.3.5 se completa normalmente.

<u>Resultado real</u>:

Durante la actualización, aparece el siguiente error:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Soluciones

* Si estaba actualizando a Adobe Commerce (todos los métodos de implementación)/Magneto Open Source versión 2.3.5, **actualice a la versión 2.3.5-p1**. Adobe Commerce (todos los métodos de implementación)/Magento Open Source versión 2.3.5-p1 reemplaza a 2.3.5.
* Si estaba actualizando a Adobe Commerce (todos los métodos de implementación)/Magento Open Source versión 2.3.4-p1, **actualice a la versión 2.3.4-p2**. Adobe Commerce (todos los métodos de implementación)/Magneto Open Source versión 2.3.4-p2 reemplaza a la versión 2.3.4-p1.

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [guía de Adobe Commerce sobre infraestructura en la nube](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce en la infraestructura en la nube: Actualización de la versión de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce local y Magento Open Source: Actualización de la aplicación y los módulos de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/overview)
* [Página de configuración de elementos de lista de deseos](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts#wishlist-item-configure-page)
* [Módulos que proporcionan informes avanzados](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
