---
title: Adobe Commerce actualización 2.4.3, 2.3.7-p1 PHP Error fatal revisión
description: 'Este artículo proporciona una corrección para los casos en los que los comerciantes intentan actualizar a Adobe Commerce (todos los métodos de implementación) o Magento Open Source 2.4.3 o 2.3.7-p1 y ven el siguiente error:'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
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
source-wordcount: '333'
ht-degree: 0%
---
# Adobe Commerce actualización 2.4.3, 2.3.7-p1 PHP Error fatal revisión

Este artículo proporciona una corrección para los casos en los que los comerciantes intentan actualizar a Adobe Commerce (todos los métodos de implementación) o Magento Open Source 2.4.3 o 2.3.7-p1 y ven el siguiente error:

*Error grave de PHP: Error no detectado: Llamada a la función indefinida Magento\Framework\Filesystem\Directory\str_contains() en &lt;...>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

El problema se solucionará en el ámbito de las versiones 2.4.4, 2.4.3-p1 y 2.3.7-p2.

## Versiones y productos afectados

* Adobe Commerce (todos los métodos de implementación) al actualizar a 2.3.7-p1 o 2.4.3.
* Magento Open Source al actualizar a 2.3.7-p1 o 2.4.3.

## Problema

El problema se debe a que las nuevas versiones de Adobe Commerce 2.4.3 y 2.3.7-p1 utilizan la función exclusiva de PHP 8 `str_contains`. Adobe Commerce 2.4.3 y 2.3.7-p1 solo son compatibles con PHP 7.4, por lo que esta función no se puede utilizar.

<u>Pasos a seguir</u> :

Intentar actualizar a Adobe Commerce 2.4.3 o 2.3.7-p1.

<u>Resultado esperado:</u>

Actualización correcta.

<u>Resultado real:</u>

Error grave de PHP.

## Solución

Como solución alternativa, ejecute el siguiente comando en CLI/Terminal: `composer require symfony/polyfill-php80` desde la carpeta raíz de Magento o instale una revisión de compositor.

Para solucionar el problema de la versión 2.4.3, Adobe Commerce (todos los métodos de implementación) y los comerciantes de Magento Open Source deben aplicar el parche:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Para solucionar el problema con 2.3.7-p1, Adobe Commerce (todos los métodos de implementación) y los comerciantes de Magento Open Source deben aplicar el parche:

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por Magento](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) para obtener instrucciones.

## Lectura relacionada

GitHub [Comando PHP 8 no compatible en Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
