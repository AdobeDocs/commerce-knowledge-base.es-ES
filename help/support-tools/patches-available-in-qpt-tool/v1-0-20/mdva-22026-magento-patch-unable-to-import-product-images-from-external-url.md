---
title: "MDVA-22026: No se pueden importar imágenes de productos desde una dirección URL externa"
description: El parche MDVA-22026 soluciona el problema de no poder importar imágenes de productos desde una URL externa.
exl-id: 29043c6c-daf2-4925-85bf-49eeeee3742c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# MDVA-22026: No se pueden importar imágenes de productos desde una dirección URL externa

El parche MDVA-22026 soluciona el problema de no poder importar imágenes de productos desde una URL externa.

Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. El ID del parche es MDVA-22026. Tenga en cuenta que el problema se corrigió en la versión 2.3.4 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.3.2-p2

**Compatible con versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.2-2.3.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. En Administración, vaya a **Sistema** > **Importar**.
1. Establecer **Tipo de entidad** = *Productos*.
1. Establecer **comportamiento de importación** = *Agregar/Actualizar*.
1. Establecer **Recuento de errores permitidos** = *10000*.
1. Seleccione el archivo que desea importar.
1. Haga clic en el botón **Comprobar datos** (que debería validar el archivo).
1. Haga clic en el botón **Importar**.

<u>Resultados esperados</u>:

Importación correcta de productos desde archivos CSV, incluidas imágenes de direcciones URL externas, según lo esperado.

<u>Resultados reales</u>:

La importación de productos desde archivos CSV, incluidas imágenes de direcciones URL externas, no se ha realizado correctamente y recibe un error similar:

```php
1. Imported resource (image) could not be downloaded from external resource due to timeout or access permissions in row(s): 4, 5, 8, 9, 16, 18, 20, 21, 22, 23, 26, 27, 28, 52, 53, 55, 58, 63, 70, 71, 77, 78, 83, 84, 91
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html).
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe el parche para el problema de Adobe Commerce con la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
