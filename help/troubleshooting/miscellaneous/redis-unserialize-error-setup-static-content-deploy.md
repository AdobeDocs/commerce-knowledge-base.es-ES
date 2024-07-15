---
title: Error de eliminación de serialización de redis `setup:static-content:deploy`
description: Este artículo proporciona una corrección para el error Redis unserialize al ejecutar `magento setup:static-content:deploy`.
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Error al anular la serialización `setup:static-content:deploy`

Este artículo proporciona una corrección para el error Redis unserialize al ejecutar `magento setup:static-content:deploy`.

La ejecución de `magento setup:static-content:deploy` causa el error de Redis:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

El problema se debe a procesos de interferencia paralelos en la conexión Redis.

Para resolver el problema, ejecute `setup:static-content:deploy` en modo de subproceso único estableciendo la siguiente variable de entorno:

```
STATIC_CONTENT_THREADS =1
```

o bien, ejecute el comando `setup:static-content:deploy` seguido del argumento `-j 1` (o `--jobs=1` ).

Tenga en cuenta que deshabilitar el subprocesamiento múltiple ralentiza el proceso de implementación de recursos estáticos.

## Versiones afectadas

* Adobe Commerce local: 2.1.2 y posterior
* Adobe Commerce en la nube 2.1.2 y versiones posteriores
* Redis, cualquier versión

## Problema

La ejecución del comando `setup:static-content:deploy` provoca el siguiente error de Redis:

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## Causa

El problema se debe a procesos de interferencia paralelos en la conexión de Redis.

Aquí, un proceso de `App/Config/Type/System.php` esperaba una respuesta para `system_defaultweb`, pero recibió una respuesta para `system_cache_exists` realizada por un proceso diferente. Vea la explicación detallada en la publicación de [Jason Woods](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Solución

Deshabilite el paralelismo y ejecute `setup:static-content:deploy` en modo de un solo subproceso estableciendo la siguiente variable de entorno:

```
STATIC_CONTENT_THREADS =1
```

También puede ejecutar el comando `setup:static-content:deploy` seguido del argumento `-j 1` (o `--jobs=1`).

>[!NOTE]
>
>En el modo de un solo subproceso, el proceso de implementación del contenido estático puede tardar cuatro veces más.

## Más información

En nuestra documentación para desarrolladores:

* [Configurar Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [Actualización de línea de comandos](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
