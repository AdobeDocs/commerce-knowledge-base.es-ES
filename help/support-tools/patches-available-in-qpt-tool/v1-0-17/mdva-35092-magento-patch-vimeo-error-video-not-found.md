---
title: 'MDVA-35092: Error de Vimeo: "No se encontró el vídeo"'
description: '''El parche de MDVA-35092 soluciona el problema donde se ve el error: *"No se encontró el vídeo"*. Este mensaje de error se muestra al introducir un vídeo de Vimeo mediante la interfaz nativa Añadir vídeo en el administrador de productos de Adobe Commerce. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3."'
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092: Error de Vimeo: &quot;No se encontró el vídeo&quot;

La revisión MDVA-35092 corrige el problema donde se ve el error: *&quot;No se encontró el vídeo&quot;*. Este mensaje de error se muestra al introducir un vídeo de Vimeo mediante la interfaz nativa Añadir vídeo en el administrador de productos de Adobe Commerce. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.5 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La API simple de Vimeo deja de funcionar según lo esperado.

<u>Pasos a seguir</u>:

1. Inicie sesión en Admin.
1. Para editar un producto existente, ve a **CATÁLOGO** > **Productos** > **Editar**, o para crear un nuevo producto, ve a **CATÁLOGO** > **Productos** > **Editar** > **Agregar producto**.
1. Haga clic en la ficha **Imágenes y vídeos** de la página de productos.
1. Haga clic en **Agregar vídeo** y agregue la URL de un vídeo de Vimeo. Haga clic en **Guardar**.

<u>Resultados esperados</u>:

El nuevo vídeo se encuentra y se guarda.

<u>Resultados reales</u>:

Error: *&quot;No se encontró el vídeo&quot;* se muestra.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
