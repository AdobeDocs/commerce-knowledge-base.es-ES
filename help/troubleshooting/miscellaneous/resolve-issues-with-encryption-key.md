---
title: Resolver problemas con la clave de cifrado
description: Este artículo explica cómo solucionar los problemas causados por la clave de cifrado que no se mueve junto con el volcado de la base de datos al otro entorno.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: bee0263da487399ab07bf9158c4d60ab316d6ea1
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Resolver problemas con la clave de cifrado

Este artículo explica cómo solucionar los problemas causados por la clave de cifrado que no se mueve junto con el volcado de la base de datos al otro entorno.

## Productos y versiones afectados

* Adobe Commerce en cloud Infrastructure 2.2.x, 2.3.x

## Problema

Después de importar un [volcado base datos](/help/how-to/general/create-database-dump-on-cloud.md) desde Producción hasta Entornos de ensayo/integración, los números de tarjeta de crédito guardados parecen incorrectos y/o los pagos fallan en integraciones de pago que requieren el uso de credenciales de comerciante.

## Causa

La clave de cifrado utilizada para cifrar datos confidenciales, como números de tarjetas de crédito y credenciales de comerciante, no se almacena en la base de datos y, por lo tanto, no se transfiere a otro entorno después de la importación o exportación del volcado de la base de datos.

## Solución

Debe copiar la clave de cifrado del entorno de origen y agregarla al entorno de destino.

Para copiar la clave de cifrado:

1. SSH al proyecto que fue el origen del volcado de la base de datos, como se describe en [SSH al entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) en nuestra documentación para desarrolladores.
1. Abrir `app/etc/env.php` en un editor de texto.
1. Copie el valor de `key` para `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Para establecer el valor clave del proyecto de destino:

1. Abra el [Consola de nube](https://console.adobecommerce.com) y busque el proyecto.
1. Establezca el valor del [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) (en nuestra documentación para desarrolladores), tal como se describe en [Configuración del proyecto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) en nuestra documentación para desarrolladores. Esto almacenará en déclencheur el proceso de implementación y `CRYPT_KEY` se anularán en el `app/etc/env.php` en cada implementación.

De forma opcional, puede anular manualmente la clave de cifrado en `app/etc/env.php` archivo:

1. SSH al entorno de destino.
1. Abrir `app/etc/env.php` en un editor de texto.
1. Pegue los datos copiados como `key` valor de `crypt`.
1. Guarde los elementos editados `env.php`.
1. Limpie la caché en el entorno de destino ejecutando `bin/magento cache:clean` o en el Administrador de Commerce, en **Sistema** > **Herramientas** > **Administración de caché**.
