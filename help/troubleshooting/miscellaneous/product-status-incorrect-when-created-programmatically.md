---
title: Estado del producto incorrecto cuando se crea mediante programación
description: Este artículo proporciona una corrección cuando el estado del producto es Deshabilitado y los productos no se muestran en la tienda o se asignan a vistas de tienda incorrectas cuando se crean o actualizan mediante programación.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Estado del producto incorrecto cuando se crea mediante programación

Este artículo proporciona una corrección cuando el estado del producto es Deshabilitado y los productos no se muestran en la tienda o se asignan a vistas de tienda incorrectas cuando se crean o actualizan mediante programación.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube 2.X.X
* Adobe Commerce local 2.X.X

## Problema

Cuando se crean o actualizan los productos del catálogo mediante programación a partir de una secuencia de comandos con la aplicación Adobe Commerce arrancada, los productos pueden tener el estado Deshabilitado o asignado a las vistas de tienda incorrectas.

## Causa

El problema podría aparecer debido a las restricciones ACL establecidas para los roles de administrador de instancias de Adobe Commerce. En el caso de una aplicación de arranque, no habrá sesiones de administración inicializadas con la configuración de ACL adecuada. Esto provocará que las validaciones no se realicen correctamente en el módulo `Magento_AdminGws`, que es responsable de la comprobación de permisos en dichas acciones.

## Solución para un estado de producto incorrecto

Establezca una preferencia de ID dinámico para `Magento\Framework\Authorization\PolicyInterface`, tal como se describe en el tema [ObjectManager>Actualizaciones programáticas del producto](https://developer.adobe.com/commerce/php/development/components/object-manager/) de nuestra documentación para desarrolladores.

## Lectura relacionada

* [Github: no se puede cambiar el estado del producto creado con productRepository](https://github.com/magento/magento2/issues/5664)
