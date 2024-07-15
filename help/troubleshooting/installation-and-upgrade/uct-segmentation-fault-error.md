---
title: Solucionar errores de la herramienta de compatibilidad de actualización
description: Este artículo explica los errores que puede experimentar al utilizar la herramienta de compatibilidad de actualización y proporciona soluciones para corregirlos y que así pueda ejecutar correctamente la herramienta.
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Solucionar errores de la herramienta de compatibilidad de actualización

Este artículo explica los errores que puede experimentar al utilizar la herramienta de compatibilidad de actualización y proporciona soluciones para corregirlos y que así pueda ejecutar correctamente la herramienta.

## Productos y versiones afectados

* [La herramienta de compatibilidad de actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) es compatible con las versiones de Adobe Commerce a partir de la 2.3.0.

## Error de segmentación

<u>Causa</u>:

Cuando dos módulos tienen el mismo nombre, la herramienta de compatibilidad de actualización muestra un error de segmentación.

<u>Solución</u>:

Para evitar este error, se recomienda especificar la ruta al módulo como argumento:

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> Es posible que la herramienta de compatibilidad de actualización no pueda analizar la base de código si contiene dependencia circular entre métodos.

## Salida vacía

<u>Pasos a seguir</u>:

1. Si después de ejecutar este comando:

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. El único resultado es `Upgrade compatibility tool`:

   ```terminal
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>Causa</u>:

La causa probable es una limitación de la memoria PHP.

Hay dos soluciones posibles para evitar esta limitación de memoria PHP.

<u>Solución 1</u>:

Anule la limitación de memoria estableciendo `memory_limit` en `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> `M2_VERSION` es la versión de Adobe Commerce de destino que desea comparar con la instancia de Adobe Commerce.

<u>Solución 2</u>:

Añadir la opción `-m` permite que la herramienta de compatibilidad de actualización analice cada módulo específico de forma independiente para evitar encontrar dos módulos con el mismo nombre en la instancia de Adobe Commerce.

Esta opción de comando también permite a la herramienta de compatibilidad de actualización analizar una carpeta que contiene varios módulos:

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

Consulte la página [Ejecutar la herramienta en una interfaz de línea de comandos](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html) para obtener más información sobre las opciones de la interfaz de línea de comandos.
