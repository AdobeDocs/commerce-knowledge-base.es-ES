---
title: "MDVA-33606: Los usuarios reciben un error al guardar la página de CMS asignada a la jerarquía"
description: El parche MDVA-33606 resuelve el problema en el que los usuarios obtienen el error "Infracción de restricción única encontrada" al guardar una página de CMS asignada al árbol de jerarquía. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3. El ID del parche es MDVA-33606. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: cdefece5-6d13-4003-87e9-810c665e940c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-33606: Los usuarios reciben un error al guardar la página de CMS asignada a la jerarquía

El parche MDVA-33606 resuelve el problema en el que los usuarios reciben *Infracción de restricción única encontrada* error al guardar una página de CMS asignada al árbol de jerarquía. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 está instalado. El ID del parche es MDVA-33606. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al intentar guardar una página de CMS asignada al árbol de jerarquía, los usuarios reciben el siguiente mensaje de error: *Infracción de restricción única encontrada*.

<u>Pasos a seguir</u>:

1. Cree una nueva página de CMS. Establezca el ámbito en Todas las vistas de la tienda. Esta es su página 1 de CMS.
1. Crear una nueva vista de tienda. Esta es la vista de tu tienda 2.
1. Ir a **Contenido** > **Jerarquía** > Agregue el CMS Página 1 al árbol de jerarquías.
1. Cambie el ámbito a la Vista de tienda 2.
   * Desmarque &quot;Usar la jerarquía de nodos principal&quot;.
   * Agregue la página 1 de CMS a este ámbito y guárdelo.
1. Ahora cambie el ámbito a Vista de tienda predeterminada.
   * Desmarque &quot;Usar la jerarquía de nodos principal&quot;.
   * Agregue la página 1 de CMS a este ámbito y guárdelo.
1. Ir a **Contenido** > **Páginas** > **Agregar nueva página**.
   * Asigne un título a la página como Página 2.
   * En la sección Página en sitios web, asigne a Todas las vistas de tienda y a las vistas de tienda (Vista de tienda predeterminada y Vista de tienda 2) y haga clic en **Guardar página**.
1. En la página de edición de CMS, abra la pestaña Jerarquía.
   * Asigne la página 2 al nodo Store View 2, al nodo Default y al nodo All Websites.

<u>Resultados esperados</u>:

Puede asignar la página de CMS a los tres nodos sin ningún error.

<u>Resultados reales</u>:

Se obtiene el siguiente error: *Infracción de restricción única encontrada*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sección.
