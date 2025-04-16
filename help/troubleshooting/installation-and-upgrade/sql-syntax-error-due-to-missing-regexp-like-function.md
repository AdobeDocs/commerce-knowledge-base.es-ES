---
title: La actualización a B2B 1.5.2 falla con un error de sintaxis SQL debido a la falta de la función REGEXP_LIKE
description: Este artículo proporciona una revisión para el problema en el que se produce un error de sintaxis SQL debido a la función REGEXP_LIKE que falta al intentar actualizar la tabla company_structure.
feature: B2B, Upgrade
role: Admin, Developer
exl-id: c5fe316c-99e3-482e-80b5-25aaae371230
source-git-commit: f83b82a95d4592252c8923720e90733115c52d87
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# La actualización a B2B 1.5.2 falla con un error de sintaxis SQL debido a la falta de la función REGEXP_LIKE

Este artículo proporciona una revisión para el error de sintaxis SQL que se produce debido a la función `REGEXP_LIKE` que falta al intentar actualizar la tabla `company_structure`.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.4.6-px + B2B 1.5.2 con [!DNL MariaDB] 10.6
* Adobe Commerce (todos los métodos de implementación) 2.4.7-px + B2B 1.5.2 con [!DNL MariaDB] 10.6

## Problema

La actualización a la versión 1.5.2 de B2B produce un error de sintaxis SQL debido a que falta la función `REGEXP_LIKE` al intentar actualizar la tabla `company_structure`.

<u>Requisitos previos</u>:

* MariaDB 10.6
* Adobe Commerce 2.4.6x o 2.4.7x
* Versión 1.5.0 o 1.5.1 de B2B

<u>Pasos a seguir</u>:

1. Asigne una compañía a una compañía matriz para establecer la jerarquía de la compañía. Consulte [Administrar la jerarquía de la compañía](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) en la guía Adobe Commerce B2B para obtener más información.
1. Actualice B2B a la versión 1.5.2.

<u>Resultados esperados</u>:

La actualización se completa correctamente.

<u>Resultados reales</u>:

`bin/magento setup:upgrade` produce el siguiente error:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## Solución

Para resolver el problema, siga estos pasos:

1. Actualice el módulo B2B a la versión 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Aplicar el parche [ACSD-65540_B2B_1.5.2.zip](assets/ACSD-65540_B2B_1.5.2.zip) adjunto. Consulte [Cómo aplicar un parche del compositor proporcionado por Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) en nuestra base de conocimiento de asistencia para obtener instrucciones.
1. Ejecutar `bin/magento setup:upgrade`.

### Aplicación de un parche mediante parches en la nube

Para Adobe Commerce en la infraestructura en la nube, siga los pasos a continuación:

1. Actualizar la versión del módulo `cloud-patches` a 1.1.5:

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Confirme e inserte los cambios para iniciar la reimplementación. Consulte [Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en nuestra guía de Adobe Commerce en la nube para obtener instrucciones.
