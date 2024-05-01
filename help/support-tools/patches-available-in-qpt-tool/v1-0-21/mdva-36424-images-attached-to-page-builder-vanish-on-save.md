---
title: "MDVA-36424: Las imágenes adjuntas al generador de páginas se desvanecen al guardar"
description: El parche MDVA-36424 resuelve el problema de que las imágenes adjuntas a los elementos del generador de páginas desaparecen cuando la categoría se guarda por segunda vez en el caso de varios sitios web, con la URL base del sitio web predeterminado diferente de la URL de administración. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. El ID del parche es MDVA-36424. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: ae15db2d-0d9f-48c1-87e4-61da1558a57c
feature: Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-36424: las imágenes adjuntas al generador de páginas se desvanecen al guardar

El parche MDVA-36424 resuelve el problema de que las imágenes adjuntas a los elementos del generador de páginas desaparecen cuando la categoría se guarda por segunda vez en el caso de varios sitios web, con la URL base del sitio web predeterminado diferente de la URL de administración. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 está instalado. El ID del parche es MDVA-36424. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.6

**Compatible con versiones de Magento:**

Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las imágenes de medios adjuntas a los elementos del generador de páginas no se guardan si la dirección URL de base del servidor es diferente de la dirección URL de base de la tienda.

<u>Pasos a seguir</u>:

1. Cree un segundo sitio web: website2.
1. Establezca una dirección URL base diferente para sitio web2 (la dirección URL base utilizada en administración debe ser diferente de la del segundo sitio web).
1. Establezca el segundo sitio web como sitio web predeterminado (**Tiendas** > *Configuración* > **Todas las tiendas** > Seleccione el segundo sitio web > definir como *Predeterminado*).
1. Vaya a la página de categoría en el backend y luego a una vista de edición de categoría.
1. Vaya a **Contenido** > *Descripción*.
1. Agregue una columna al contenido y defina una imagen de fondo mediante la galería de medios.
1. Guarde la categoría.
1. Vaya a la **Contenido** > *Descripción* de nuevo; verá la imagen guardada correctamente.
1. Vuelva a guardar la categoría.
1. Vaya a la **Contenido** > *Descripción*.

<u>Resultados esperados</u>:

La imagen no se elimina al guardar la categoría.

<u>Resultados reales</u>:

La imagen se elimina después de guardar la categoría por segunda vez.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
