---
title: Errores de implementación al habilitar el módulo de Baler alfa inicial
description: El comerciante experimenta errores de implementación al utilizar el módulo Baler en un entorno de producción, ya que la función se encuentra actualmente en la primera fase de desarrollo alfa.
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Errores de implementación al habilitar el módulo de Baler alfa inicial

El comerciante experimenta errores de implementación al utilizar el módulo Baler en un entorno de producción, ya que la función se encuentra actualmente en la primera fase de desarrollo alfa.

>[!WARNING]
>
>El paquete de Javascript de la empacadora alfa temprana no está listo para su uso en producción y se utiliza bajo su propia responsabilidad.

## Productos y versiones afectados

* Adobe Commerce en la nube 2.3.x y 2.4.x.
* Adobe Commerce local 2.3.x y 2.4.x.

## Problema

No recomendamos que los comerciantes utilicen el módulo Baler en un entorno de producción, ya que se encuentra actualmente en la fase de desarrollo alfa inicial. Su uso puede provocar errores de implementación.

<u>Pasos a seguir</u>:

1. El comerciante intenta insertar el **SCD\_USE\_BALER** en la fase de compilación del `.magento.env.yaml` , que habilita el paquete Javascript de Baler.
1. El comerciante también agrega la dependencia del compositor de Baler: `"magento/module-baler": "1.0.0-alpha"` hasta `require` sección de `composer.json`.

<u>Resultado esperado</u>:

Implementación correcta.

<u>Resultado real</u>:

El comerciante ve el siguiente mensaje de error en los registros de implementación de la nube, que es `<project home>/var/log/cloud.log`, en la fase de implementación del contenido estático:

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## Causa

El módulo de Baler se encuentra actualmente en la fase inicial de desarrollo alfa, y el proceso de instalación de la extensión de Baler es complejo.

## Solución

Puede revisar la documentación existente del Alpha de embaladores en [Github/Magento/Baler/Introducción al alfa](https://github.com/magento/baler/blob/master/docs/ALPHA.md). Sin embargo, no está listo para su uso en producción y se utiliza bajo su propio riesgo. En su lugar, se recomienda combinar o agrupar archivos Javascript (JS) mediante el paquete integrado (paquete básico) de Adobe Commerce para la optimización de archivos.

* Puede activar la combinación o el agrupamiento en la administración (la combinación y el agrupamiento no se pueden activar al mismo tiempo): **Tiendas** > **Configuración** > **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de JavaScript**.
* También puede habilitar el paquete integrado (paquete básico) de Adobe Commerce desde la línea de comandos: `php -f bin/magento config:set dev/js/enable_js_bundling 1`

Para obtener más información, consulte [Optimización de archivos CSS y Javascript en Adobe Commerce en infraestructuras en la nube y Adobe Commerce local](https://support.magento.com/hc/en-us/articles/360044482152).
