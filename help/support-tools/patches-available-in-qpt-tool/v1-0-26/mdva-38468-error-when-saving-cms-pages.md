---
title: "MDVA-38468: Recibir un mensaje de error al guardar la página de CMS"
description: '''El parche de MDVA-38468 Adobe Commerce corrige el problema en el que los usuarios reciben el mensaje de error: * Ya existe un elemento con el mismo ID "PAGE_ID",* al guardar una página de CMS. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26. El ID del parche es MDVA-38468. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6."'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468: Recibir un mensaje de error al guardar la página de CMS

El parche de MDVA-38468 Adobe Commerce soluciona el problema en el que los usuarios reciben el mensaje de error: *Ya existe un elemento con el mismo ID &quot;PAGE_ID&quot;.* al guardar una página de CMS. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 está instalado. El ID del parche es MDVA-38468. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
Adobe Commerce en infraestructura en la nube 2.3.2-p2

**Compatible con las versiones de Adobe Commerce:**
Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.2-2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al intentar guardar una página de CMS, recibe el siguiente mensaje de error: *Ya existe un elemento con el mismo ID &quot;PAGE_ID&quot;.*

<u>Pasos a seguir</u>:

1. Cree un nuevo sitio web + tienda + vista de tienda.
1. Cree otro sitio web, una tienda o una vista de tienda.
1. Ir a **Contenido** > **Jerarquía** > Añada cualquier página de CMS existente al árbol de jerarquías.
1. Ir a **Contenido** > **Páginas** > **Agregar nueva página**:
   * Añada cualquier título.
   * En la sección Página en sitios web, asigne a ambas vistas de tienda creadas.
   * En la sección Jerarquía, asigne a cualquier categoría.
   * **Guardar y continuar Editar**.

<u>Resultados esperados</u>:

La página se guarda sin ningún error.

<u>Resultados reales</u>:

La página se guarda, pero aparece el siguiente mensaje de error: *Ya existe un elemento (Magento\VersionsCms\Model\Hierarchy\Node) con el mismo ID &quot;PAGE_ID&quot;.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
