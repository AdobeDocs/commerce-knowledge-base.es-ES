---
title: "MDVA-38308: Error tras añadir vídeos de Vimeo a productos desactivados"
description: "El parche de calidad MDVA-38308 para Adobe Commerce soluciona el problema en el que los usuarios reciben el mensaje de error: *Aviso: Índice indefinido: extensión en /lib/internal/Magento/Framework/File/Uploader.php en la línea 806,* al añadir vídeos de Vimeo a productos desactivados. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. El ID del parche es MDVA-38308. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4."
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308: Error tras añadir vídeos de Vimeo a productos desactivados

El parche de calidad MDVA-38308 para Adobe Commerce soluciona el problema en el que los usuarios reciben el mensaje de error: *Aviso: Índice indefinido: extensión en /lib/internal/Magento/Framework/File/Uploader.php en la línea 806,* al añadir vídeos de Vimeo a productos deshabilitados. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. El ID del parche es MDVA-38308. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
Adobe Commerce en infraestructura en la nube 2.4.1-p1, 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**
Adobe Commerce local y Adobe Commerce en infraestructura en la nube 2.3.5 - 2.3.6-p1, 2.4.0 - 2.4.1-p1, 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al agregar vídeos de Vimeo a productos deshabilitados, recibe el siguiente mensaje de error: *Aviso: Índice no definido: extensión en /lib/internal/Magento/Framework/File/Uploader.php en la línea 806*

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Deshabilite el producto creado.
1. Intente añadir un vídeo de Vimeo al producto desactivado.

<u>Resultados esperados</u>:

El vídeo se agrega sin ningún error.

<u>Resultados reales</u>:

Se obtiene el siguiente error:
*Aviso: Índice no definido: extensión en /lib/internal/Magento/Framework/File/Uploader.php en la línea 806*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad en nuestra base de conocimiento de asistencia, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) de nuestra base de conocimiento de asistencia.
