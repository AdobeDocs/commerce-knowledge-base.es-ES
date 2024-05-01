---
title: Adobe Commerce actualización 2.4.3, 2.3.7-p1 PHP Error fatal revisión
description: "Este artículo proporciona una corrección para los casos en los que los comerciantes intentan actualizar a Adobe Commerce (todos los métodos de implementación) o al Magento Open Source 2.4.3 o 2.3.7-p1 y ven el siguiente error:"
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Adobe Commerce actualización 2.4.3, 2.3.7-p1 PHP Error fatal revisión

Este artículo proporciona una corrección para los casos en los que los comerciantes intentan actualizar a Adobe Commerce (todos los métodos de implementación) o al Magento Open Source 2.4.3 o 2.3.7-p1 y ven el siguiente error:

*Error grave de PHP: Error no detectado: Llamada a una función indefinida Magento\Framework\Filesystem\Directory\str_contains() en &lt;...>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

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

Como solución alternativa, ejecute el siguiente comando en CLI/Terminal: `composer require symfony/polyfill-php80` desde la carpeta raíz del Magento o instale un parche de composer.

Para solucionar el problema de la versión 2.4.3, Adobe Commerce (todos los métodos de implementación) y los comerciantes de Magento Open Source deben aplicar el parche:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Para solucionar el problema con 2.3.7-p1, Adobe Commerce (todos los métodos de implementación) y los comerciantes de Magento Open Source deben aplicar el parche:

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Cómo aplicar el parche

Consulte [Cómo aplicar un parche del compositor proporcionado por el Magento](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) para obtener instrucciones.

## Lectura relacionada

GitHub [Comando PHP 8 no compatible en el #33680 Magento 2.4.3 EE](https://github.com/magento/magento2/issues/33680)
