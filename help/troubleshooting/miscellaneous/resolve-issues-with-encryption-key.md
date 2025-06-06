---
title: Resolver problemas con la clave de cifrado
description: Este artículo explica cómo solucionar los problemas causados por la clave de cifrado que no se mueve junto con el volcado de la base de datos al otro entorno.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: 0458b37e2af4c9ad2ec92a1fdd6844ef222ef84a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Resolver problemas con la clave de cifrado

Este artículo explica cómo solucionar los problemas causados por la clave de cifrado que no se mueve junto con el volcado de la base de datos al otro entorno.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube 2.4.x

## Problema

Después de importar un [volcado de la base de datos](/help/how-to/general/create-database-dump-on-cloud.md) desde los entornos Producción a Ensayo/Integración, los números de tarjeta de crédito guardados parecen incorrectos y/o los pagos fallan en las integraciones de pago que requieren el uso de credenciales de comerciante.

## Causa

La clave de cifrado utilizada para cifrar datos confidenciales, como números de tarjetas de crédito y credenciales de comerciante, no se almacena en la base de datos y, por lo tanto, no se transfiere a otro entorno después de la importación o exportación del volcado de la base de datos.

## Solución

Debe copiar la clave de cifrado del entorno de origen y agregarla al entorno de destino.

Para copiar la clave de cifrado:

1. SSH al proyecto que era la fuente del volcado de la base de datos, tal como se describe en [SSH al entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=es) en nuestra documentación para desarrolladores.
1. Abra `app/etc/env.php` en un editor de texto.
1. Copie el valor de `key` para `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Para establecer el valor clave del proyecto de destino:

1. Abra [Cloud Console](https://console.adobecommerce.com) y busque el proyecto.
1. Establezca el valor de la variable [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=es) (en nuestra documentación para desarrolladores), tal como se describe en [Configure su proyecto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=es) en nuestra documentación para desarrolladores. Esto almacenará en déclencheur el proceso de implementación y `CRYPT_KEY` se anulará en el archivo `app/etc/env.php` en cada implementación.

Opcionalmente, puede anular manualmente la clave de cifrado en el archivo `app/etc/env.php`:

1. SSH al entorno de destino.
1. Abra `app/etc/env.php` en un editor de texto.
1. Pegue los datos copiados como el valor `key` para `crypt`.
1. Guarde el(la) `env.php` editado(a).
1. Limpie la caché en el entorno de destino ejecutando `bin/magento cache:clean` o en el administrador de Commerce en **Sistema** > **Herramientas** > **Administración de caché**.
