---
title: "MDVA-36853: No se cargan imágenes de grandes galerías de medios"
description: El parche de MDVA-36853 soluciona el problema cuando no se carga ninguna imagen, ya que el widget de galería de medios del generador de páginas no se carga cuando el directorio multimedia es grande.
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853: No se cargan imágenes de grandes galerías de medios

El parche de MDVA-36853 soluciona el problema cuando no se carga ninguna imagen, ya que el widget de galería de medios del generador de páginas no se carga cuando el directorio multimedia es grande.

Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. El ID del parche es MDVA-36853. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.4.2

**Compatible con versiones de Adobe Commerce:** Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Establezca **Habilitar la Galería multimedia antigua** = *Sí* en **Administración > Tiendas > Configuración > Avanzadas > Sistema > Galería multimedia**.
1. Vaya a **Contenido > Bloques** y cree un nuevo bloque CMS o edite un bloque CMS existente.
1. Haga clic en el botón **Editar con PageBuilder**.
1. Añada un elemento multimedia.
1. Haz clic en el botón **Seleccionar de la galería**.

<u>Resultados esperados</u>:

Tanto el widget de galería de medios como las imágenes de galería de medios se cargan, según lo esperado.

<u>Resultados reales</u>:

El widget de galería de medios y las imágenes de galería de medios no se cargan cuando el directorio `pub/media/catalog/product/cache/` es grande.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en la herramienta QPT, consulte la sección [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
