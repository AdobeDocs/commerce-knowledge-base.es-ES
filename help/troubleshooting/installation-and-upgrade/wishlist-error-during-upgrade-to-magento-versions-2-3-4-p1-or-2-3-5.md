---
title: Error de lista de deseos durante la actualización a las versiones de Adobe Commerce 2.3.4-p1 o 2.3.5
description: Este artículo proporciona una corrección del problema conocido al actualizar a las versiones de Adobe Commerce 2.3.4-p1 y 2.3.5 relacionado con un error de la lista de deseos durante la actualización a estas versiones.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '332'
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

Actualice su Adobe Commerce (todos los métodos de implementación)/Magento Open Source a la versión 2.3.4-p1 o 2.3.5.

<u>Resultado esperado</u>:

El proceso de actualización a Adobe Commerce (todos los métodos de implementación)/Magento Open Source versión 2.3.4-p1 o 2.3.5 se completa normalmente.

<u>Resultado real</u>:

Durante la actualización, aparece el siguiente error:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Soluciones

* Si estaba actualizando a Adobe Commerce (todos los métodos de implementación)/Magneto Open Source versión 2.3.5, **actualice a la versión 2.3.5-p1**. Adobe Commerce (todos los métodos de implementación)/Magento Open Source versión 2.3.5-p1 sustituye a 2.3.5.
* Si estaba actualizando a Adobe Commerce (todos los métodos de implementación)/Magento Open Source versión 2.3.4-p1, **actualice a la versión 2.3.4-p2**. Adobe Commerce (todos los métodos de implementación)/Magneto Open Source versión 2.3.4-p2 reemplaza a la versión 2.3.4-p1.

## Lectura relacionada

En nuestra documentación para desarrolladores:

* [Guía de infraestructura de Adobe Commerce en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce en infraestructura en la nube - Actualizar la versión de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Magento Open Source y aplicación locales de Adobe Commerce: actualice la aplicación y los módulos de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/overview)
* [Página de configuración de elementos de lista de deseos](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts/#wishlist-item-configure-page)
* [Módulos que proporcionan informes avanzados](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
