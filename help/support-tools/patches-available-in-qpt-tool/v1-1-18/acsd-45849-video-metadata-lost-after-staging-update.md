---
title: "ACSD-45849: Los metadatos de vídeo se pierden tras la actualización del ensayo"
description: El parche ACSD-45849 corrige el problema de pérdida de metadatos de vídeo después de aplicar una actualización de ensayo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. El ID del parche es ACSD-45849. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.
exl-id: 071a535d-f96c-4731-a17c-0b7bf8a87372
feature: Staging, Page Content
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-45849: los metadatos de vídeo se pierden tras la actualización del ensayo

El parche ACSD-45849 corrige el problema de pérdida de metadatos de vídeo después de aplicar una actualización de ensayo. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalado. El ID del parche es ACSD-45849. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los metadatos de vídeo se pierden después de aplicar una actualización de ensayo.

<u>Pasos a seguir</u>:

1. Configure la clave de API de YouTube en **Administrador** > **Tiendas** > **Configuración** > **Catálogo** > **Vídeo del producto**.
1. Cree un producto con un vídeo de YouTube. Tenga en cuenta que se han rellenado la dirección URL, el título y la descripción.
1. Cree una nueva actualización programada para el producto con cualquier parámetro sin cambiar el *Imágenes y vídeo* sección.
1. Haga clic en **Ver/Editar** en Cambios programados.
1. Ir a **Imágenes y vídeos** y haga clic en el vídeo.

<u>Resultados esperados</u>:

La dirección URL, el título y la descripción contienen los datos adecuados.

<u>Resultados reales</u>:

Los campos URL, title y description están vacíos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
