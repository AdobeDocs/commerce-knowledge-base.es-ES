---
title: "ACSD-48771: el editor WYSIWYG procesa el contenido de forma diferente"
description: Aplique el parche ACSD-48771 para corregir el problema de Adobe Commerce en el que el editor WYSIWYG procesa el contenido de forma diferente.
exl-id: 6a856fa3-6099-4237-8d1c-e3735b8ca012
feature: Cache, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-48771: el editor WYSIWYG procesa el contenido de forma diferente

El parche ACSD-48771 corrige el problema en el que el editor WYSIWYG procesa el contenido de forma diferente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. El ID del parche es ACSD-48771. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El editor WYSIWYG procesa el contenido de forma diferente.

<u>Pasos a seguir</u>:

1. Vaya al Administrador de Adobe Commerce, cree una nueva página con una fila de tres columnas y guarde la página.
1. Actualice Adobe Commerce a una de las versiones más recientes.
1. Configure el explorador [!DNL Chrome] para deshabilitar la caché y la velocidad a *Fast 3G*.
1. Vuelva a la página de edición y actualícela hasta que las columnas se conviertan en filas.
1. Guarde la página mientras las columnas están en filas.

<u>Resultados esperados</u>:

El generador de páginas de administración no debe mostrar columnas en filas.

<u>Resultados reales</u>:

Las columnas aparecen en filas diferentes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
