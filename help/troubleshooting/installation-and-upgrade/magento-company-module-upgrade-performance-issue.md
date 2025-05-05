---
title: Problema de rendimiento en la actualización del módulo Magento_Company después de la actualización B2B 1.5.2
description: Este artículo proporciona una revisión para el problema de rendimiento en la actualización del módulo Magento_Company después de la actualización B2B 1.5.2, que aborda el tiempo de procesamiento excesivamente largo para grandes conjuntos de datos en la tabla company_structure.
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Problema de rendimiento en la actualización del módulo Magento_Company después de la actualización B2B 1.5.2

Este artículo proporciona una revisión para el problema de rendimiento en la actualización del módulo `Magento_Company` después de la actualización B2B 1.5.2, que aborda el tiempo de procesamiento excesivamente largo para conjuntos de datos grandes (más de 100 000 registros) en la tabla `company_structure`.

## Productos y versiones afectados

* Adobe Commerce (todos los métodos de implementación) 2.4.6-px + B2B 1.5.2
* Adobe Commerce (todos los métodos de implementación) 2.4.7-px + B2B 1.5.2
* Adobe Commerce (todos los métodos de implementación) 2.4.8 + B2B 1.5.2

## Problema

Actualizar el módulo `Magento_Company` después de actualizar a B2B 1.5.2 lleva un tiempo excesivamente largo al procesar un gran número de registros (~100.000+) en la tabla `company_structure`.

<u>Requisitos previos</u>:

* Debe instalarse ACSD-65540_B2B_1.5.2.patch.
* Adobe Commerce 2.4.6: 2.4.8
* Versión 1.5.0, 1.5.1 o B2B 1.5.2 de B2B con el parche ACSD-65540 aplicado

<u>Pasos a seguir</u>:

1. Asigne una compañía a una compañía matriz para establecer la jerarquía de la compañía. Consulte [Administrar la jerarquía de la compañía](https://experienceleague.adobe.com/es/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) en la guía Adobe Commerce B2B para obtener más información.
1. Actualice B2B a la versión 1.5.2.

<u>Resultados esperados</u>:

La actualización se completa correctamente.

<u>Resultados reales</u>:

La actualización del módulo `Magento_Company` tarda mucho tiempo en completarse si hay muchos registros en la tabla `company_structure`.

## Solución

Para resolver el problema, siga estos pasos:

1. Actualice el módulo B2B a la versión 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Aplique el [ACSD-65540_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip).

1. Aplique el [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip) adjunto.
1. Ejecute `bin/magento setup:upgrade` después de aplicar el parche.

### Cómo aplicar el parche

Descomprima el archivo y vea [Cómo aplicar un parche del compositor proporcionado por Adobe](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) en nuestra base de conocimiento de asistencia para obtener instrucciones.

### Aplicación de un parche mediante parches en la nube

Para comerciantes de Adobe Commerce en la nube, siga los pasos a continuación:

1. Actualice la versión del módulo cloud-patch a 1.1.5 para instalar el ACSD-65540_B2B_1.5.2.patch distribuido como MCLOUD-13605.

   >[!NOTE]
   >
   >Para comprobar si el parche ya está instalado, ejecute:
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Agregue el parche ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch al directorio `m2-hotfixes`.
1. Confirme e inserte los cambios para iniciar la reimplementación y `bin/magento setup:upgrade`. Consulte [Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en nuestra guía de Adobe Commerce en la nube para obtener instrucciones.

## Lectura relacionada

* [La actualización a B2B 1.5.2 falla con un error de sintaxis SQL debido a que falta la función REGEXP_LIKE](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)
