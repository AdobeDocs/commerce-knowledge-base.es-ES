---
title: "Error en la actualización del compositor en Adobe Commerce: tipo de argumento incompatible"
description: Este artículo proporciona una solución para los casos en los que la implementación está atascada porque hay un problema con la compilación del código. Este problema se debe a una nueva versión de dependencia de symfony/console (4.4.27, 4.4.28).
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Error en la actualización del compositor en Adobe Commerce: tipo de argumento incompatible

>[!NOTE]
>
>Este problema se ha corregido en la última versión de symfony 4.4.29.

Este artículo proporciona una solución para los casos en los que la implementación está atascada porque hay un problema con la compilación del código. Este problema se debe a una nueva versión de dependencia de symfony/console (4.4.27, 4.4.28).

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) y Magento Open Source:
   * 2.4.0, 2.4.0-p1, 2.4.1, 2.4.1-p1, 2.4.2, 2.4.2-p1, 2.4.2-p2, 2.4.3
   * 2.3.5, 2.3.5-p1, 2.3.5-p2, 2.3.6, 2.3.6-p1, 2.3.7, 2.3.7-p1
* dependencia de symfony/console (4.4.27, 4.4.28).

## Problema

Una nueva versión de symfony/console dependencies (4.4.27, 4.4.28) está causando que el proceso de compilación de dependencias falle.

<u>Pasos a seguir</u>:

Al instalar o actualizar Adobe Commerce o ejecutar la actualización del compositor, la ejecución falla con el siguiente mensaje de error:
*Tipo de argumento no compatible: Tipo requerido: int. Tipo real: cadena*

## Causa

El problema se debe a la incompatibilidad del código principal de Adobe Commerce con la última dependencia &quot;symfony/console&quot; publicada en las versiones 4.4.27 y 4.4.28.

## Solución

El problema se resolverá automáticamente una vez que se publique una nueva versión 4.2.29 de symfony/console (que se espera para agosto de 2021).

**Corrección en Adobe Commerce local:**

Adobe Commerce local 2.4.x

Ejecute el siguiente comando en CLI/Terminal:

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

Todos los comerciantes locales de Adobe Commerce 2.3.5+ deben ejecutar el siguiente comando de CLI:

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**Corrección en Adobe Commerce en la infraestructura en la nube:**

Ejecute los comandos anteriores o actualice a la última versión de herramientas ECE (ece-tools: 2002.1.7), que estará disponible el jueves 29 de julio. Para ver los pasos, consulte [Cloud for Adobe Commerce > Actualizar ece-tools version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) en nuestra documentación para desarrolladores.

La corrección completa se publicará en Adobe Commerce (todos los métodos de implementación) 2.4.4.

## Lectura relacionada

* Github: [2021-07-27 Actualización del compositor Tipo de argumento incompatible: Tipo requerido: int. Tipo real: cadena](https://github.com/magento/magento2/issues/33595)
