---
title: La implementación falla porque el módulo de Fastly es incompatible con la versión Adobe Commerce
description: 'ACTUALIZADO: 29 de febrero de 2019'
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# La implementación falla porque el módulo de Fastly es incompatible con la versión Adobe Commerce

ACTUALIZACIÓN: 29 de febrero de 2019

Este artículo proporciona una corrección para los casos en los que la implementación falla porque el módulo de Fastly no es compatible con la versión actual de Adobe Commerce.

**Problema:** La implementación falla después de una nueva confirmación y inserción, con un mensaje de error similar al siguiente:

>\[Exception\] Advertencia: Falta el argumento 3 para Fastly\\Cdn\\Plugin\\..., llamado en /app/vendor/magento/framework/Interception/Interceptor.php ... y definido en /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php ...

**Causa:** cambios incompatibles con versiones anteriores en el módulo Fastly v1.2.79.

**Solución (temporal):** actualice el módulo Fastly a la versión 1.2.82 o superior y cargue un nuevo VCL en el administrador de Commerce. A continuación, confirme e inserte los cambios para almacenar en déclencheur una implementación correcta.

## Versiones afectadas

* Adobe Commerce local 2.1.X
* Adobe Commerce en la infraestructura en la nube 2.1.X
* Módulo Fastly 1.2.79

## Problema

Cuando confirma e inserta los cambios en el entorno de integración, producción o ensayo, normalmente el siguiente paso es activar el proceso de implementación. Esto se realiza automáticamente en Adobe Commerce en la edición de infraestructura en la nube y manualmente en Adobe Commerce local.

Es posible que la implementación falle con los siguientes mensajes de error:

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

Si usa Adobe Commerce en la solución de infraestructura en la nube, verá este mensaje de error en el [registro de implementación](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/test/log-locations). Para Adobe Commerce local, verá el error en la línea de comandos.

## Causa

El problema se debe a los cambios incompatibles con versiones anteriores en el módulo Fastly v1.2.79.

## Solución

Actualice el módulo Fastly a la versión 1.2.82 o superior.

Para ello, siga los siguientes pasos:

1. Ejecute uno de los siguientes comandos:
   * si el módulo Fastly se incluye en el metapaquete de nube de magento:    <pre>composer update magento/magento-cloud-metapackage</pre>
   * si el módulo de Fastly se instaló por separado (por ejemplo, en caso de que utilice Adobe Commerce local, no la edición en la nube) <pre>actualización del compositor de fastly/magento2</pre>
1. Confirme e inserte los cambios y almacene en déclencheur el proceso de implementación si no se realiza automáticamente.
1. En el Administrador, [cargue la nueva VCL a Fastly](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
