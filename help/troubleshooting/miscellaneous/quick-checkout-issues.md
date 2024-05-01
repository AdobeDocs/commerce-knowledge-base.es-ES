---
title: Solucionar problemas de cierre rápido
description: Este artículo explica los problemas que puede experimentar al utilizar la extensión Cierre de compra rápido para Adobe Commerce y proporciona soluciones para solucionarlos de modo que pueda utilizar correctamente la extensión.
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Solucionar problemas de cierre rápido

Este artículo explica los problemas que puede experimentar al utilizar la extensión Cierre de compra rápido para Adobe Commerce y proporciona soluciones para solucionarlos de modo que pueda utilizar correctamente la extensión.

## Productos y versiones afectados

* El [Cierre de compra rápido](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) es compatible tanto con Magento Open Source como con Adobe Commerce. Consulte [Política de ciclo vital](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) para obtener más información sobre las versiones compatibles.

## Teclas de composición y estabilidad mínima incorrectas para `RC`

<u>Causa</u>:

Si ve el siguiente mensaje de error, puede que tenga claves de composición incorrectas:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>Solución</u>:

Compruebe que las claves del compositor están vinculadas al _ID de Magento_ se utiliza durante el registro Cierre de compra rápido.

Para ver qué claves de composición están configuradas:

1. Buscar la ubicación de `auth.json` archivo:

   ```bash
   composer config --global home
   ```

1. Ver el `auth.json` archivo:

   ```bash
   cat /path/to/auth.json
   ```

1. Consulte [qué claves están asociadas a su ID de Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. Establezca la estabilidad mínima en `RC` en el `composer.json` archivo.

   ```json
   "minimum-stability": "RC"
   ```

## Memoria insuficiente para PHP

<u>Causa</u>:

Si ve el siguiente mensaje de error que indica que no tiene suficiente memoria para PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>Solución</u>:

[Aumento del límite de memoria](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) para PHP en su entorno en `php.ini`.

Como alternativa, puede especificar el límite de memoria mediante este comando: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Por ejemplo:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Agregar líneas de dirección de calle con una nueva dirección de envío

Hay un problema conocido con la extensión de cierre de compra rápido.

Cuando usted [inicie sesión con una cuenta de Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/), puede agregar una nueva dirección de envío con una limitación de 4 líneas por dirección de calle.

Si la nueva dirección de envío contiene más de 4 líneas, no se almacenan.

Adobe Commerce suele configurarse para admitir hasta 20 líneas de direcciones de calle.

## Comportamiento inesperado al `Display Billing Address On` se establece en `payment page`

Hay un problema conocido con la extensión de cierre de compra rápido.

Si establece la variable `Display Billing Address On` al parámetro `payment page` y [inicie sesión con una cuenta de Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) cuando marque la `My billing and shipping address are the same` , aparece el botón de opción `use existing card`. Como la dirección de facturación solo es aplicable a las nuevas tarjetas de crédito, la dirección no será visible hasta que el usuario de Bolt decida añadir una nueva opción de tarjeta de crédito.

Consulte la [Finalizar compra](https://docs.magento.com/user-guide/configuration/sales/checkout.html) tema para obtener más información sobre `Display Billing Address On` parámetro.
