---
title: Retrasar el inicio de sesión o cierre de compra del administrador de Commerce
description: Este artículo proporciona una corrección del problema al iniciar sesión en el administrador de Commerce o al abrir la página de cierre de compra, que causa un retraso o tiempo de espera (más de 30 segundos). El problema se produce cuando Redis se utiliza para el almacenamiento de sesión.
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: aa8c32e3524d669daea7bcf8bc63ed9f8ed16ffa
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Retrasar el inicio de sesión o cierre de compra del administrador de Commerce

Este artículo proporciona una corrección del problema al iniciar sesión en el administrador de Commerce o al abrir la página de cierre de compra, que causa un retraso o tiempo de espera (más de 30 segundos). El problema se produce cuando Redis se utiliza para el almacenamiento de sesión.

**Causa:**   [Problema de GitHub \#12385](https://github.com/magento/magento2/issues/12385).

**Solución:** actualice el parche de Adobe Commerce más reciente para corregir estos problemas en todas las versiones de Redis y en versiones específicas de Adobe Commerce.

## Versiones y tecnologías afectadas

* Adobe Commerce en las versiones de infraestructura en la nube 2.1.11, 2.1.13 y 2.2.1
* Versiones locales de Adobe Commerce 2.1.11, 2.1.13 y 2.2.1
* Redis, todas las versiones

Si usa Adobe Commerce en la versión de infraestructura en la nube [2.2.0](#h_64593789291526919876198), encontrará una solución.

## Problema

El inicio de sesión en el administrador de Commerce o el inicio de sesión en la página de cierre de compra tardan más de 30 segundos.

Esto solo ocurre cuando las sesiones de usuario se almacenan en Redis.

## Causa

Adobe Commerce tuvo un problema con el mecanismo de bloqueo de sesión que agregaba un tiempo de espera de 30 segundos a algunas operaciones cuando Redis se utilizaba para el almacenamiento de sesión. Para obtener más información, consulte el [problema de Github \#12385](https://github.com/magento/magento2/issues/12385).

Este problema se ha corregido en Adobe Commerce 2.1.14 y 2.2.2.

## Soluciones: revisión o actualización

### Solución 1: aplique el parche con una corrección

Para recibir un parche, [envía un ticket de asistencia](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando el parche. En su ticket, especifique su versión de Adobe Commerce y el número de referencia correspondiente para el parche:

* **2.1.11 y versiones posteriores:** MDVA-7835
* **2.2.1:** MDVA-8128

El número de referencia general (independiente de la versión) es MAGETWO-84289.

### Solución 2: actualice a 2.1.14/2.2.2 o posterior

Si anteriormente ha considerado actualizar a Adobe Commerce 2.2.2 o posterior, puede utilizar esta oportunidad de actualización para solucionar el problema.

## Solución alternativa: deshabilitar el bloqueo de sesión

Para deshabilitar el bloqueo de sesión, establezca `disable_locking` en `1` en la sección de configuración de Redis del archivo `env.php`:

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

Esta solución no afecta a ninguna otra funcionalidad de Adobe Commerce.

### Revertir solución tras aplicar el parche

Después de aplicar la revisión con la corrección, ya no es necesaria la solución, por lo que puede revertirla (establecer `disable_locking` en `0`).

## Adobe Commerce en la infraestructura en la nube 2.2.0: utilice ECE-Tools v2002.0.8 o posterior {#h_64593789291526919876198}

El paquete de script de implementación [ECE-Tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html) con las versiones 2002.0.3 - 2002.0.7 [aplica](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) la solución automáticamente, estableciendo `disable_locking` en `1`. Esto deshabilita el mecanismo de bloqueo de sesión para Adobe Commerce 2.2.0, en el que no se produce el problema original.

Si está ejecutando Adobe Commerce en la infraestructura en la nube 2.2.0, actualice ECE-Tools a v2002.0.8 o posterior. También puede considerar actualizar su Adobe Commerce en la infraestructura en la nube a la versión 2.2.2 o posterior.
