---
title: El parche no encontró errores durante la implementación o la aplicación manual
description: 'Este artículo proporciona una solución al problema en el que ve un error. *No se encontraron los siguientes parches: MDVA-XXXXX, ACSD-XXXXX. Compruebe la disponibilidad de estos parches para la versión actual de Magento utilizando el comando "status"*.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: 180f0e00ec1a2c6c3bd2ebca4dafe387c7bb3852
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# El parche no encontró errores durante la implementación o la aplicación manual

Este artículo proporciona una solución al problema que se produce al actualizar la instancia cuando falla la implementación y ve un error en los registros de implementación: *No se encontraron los siguientes parches: MDVA-XXXXX, ACSD-XXXXX. Compruebe la disponibilidad de estos parches para la versión actual de Magento mediante el comando &quot;status&quot;*.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, [todas las versiones compatibles](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Se produjo un error al actualizar Adobe Commerce: *No se encontraron las siguientes revisiones*.

## Causa

Los parches aplicados anteriormente a sus versiones anteriores no son aplicables o ya no están disponibles para su nueva versión.

Este problema también puede ocurrir cuando el paquete instalado de la herramienta Parches de calidad (`magento/quality-patches`) está obsoleto.

Por ejemplo:

Caso 1:
* Un parche puede haber estado disponible originalmente para 2.4.7-p9 en QPT 1.1.71
* Una versión más reciente de QPT (por ejemplo, 1.1.72) puede añadir más tarde compatibilidad con 2.4.7-p10
* Si el cliente actualiza Commerce a la versión 2.4.7-p10 pero mantiene instalada una versión anterior de QPT, QPT puede no reconocer que existe una variante de parche compatible para 2.4.7-p10

Caso 2:
* Se puede haber añadido un parche en QPT 1.1.72
* Si el cliente mantiene instalada una versión anterior de QPT, QPT no reconocerá que el parche existe

En estos casos, la aplicación del parche puede fallar con un mensaje como:

```
Next patches weren't found: ACSD-12345.
Check the availability of these patches for the  current Magento version using the "status" command.
```

Esto sucede porque la versión instalada de QPT no puede asignar la versión actual de Commerce a una versión aplicable del parche.

## Solución

Este problema no se limita a las implementaciones que aplican parches a través de `.magento.env.yaml`. El mismo problema subyacente también puede ocurrir al aplicar un parche manualmente con:

```bash
vendor/bin/magento-patches apply <PATCH_ID>
```

Por ejemplo:

```
Next patches weren't found: ACSD-12345
Check the availability of these patches for the  current Magento version using the "status" command.
```

En este caso, el parche no está disponible para la versión de Adobe Commerce instalada en el entorno donde se está ejecutando el comando.

1. Compruebe su archivo de `.magento.env.yaml` en la sección QUALITY_PATCHES, por ejemplo:

   ```yaml
   QUALITY_PATCHES:
    * MDVA-XXXXX
    * ACSD-XXXXX
   ```

1. Busque los identificadores de los parches en las [Notas de la versión de parches de calidad](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=es) para comprobar si se pueden aplicar a la nueva versión de Adobe Commerce a la que está actualizando.
1. Si el parche no se aplica a la nueva versión de Adobe Commerce a la que desea actualizar, quite el identificador del parche del archivo `.magento.env.yaml`.
1. Una vez que haya revisado todos los ID de parche indicados por el error, inserte los cambios y vuelva a implementar.

## Lectura relacionada

* [Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es#apply-a-patch-in-a-local-environment) en la Guía de infraestructura de Commerce en la nube.
