---
title: "MDVA-34695: Productos y categorías que no se muestran"
description: El parche MDVA-34695 resuelve el problema de que los productos y las categorías no se muestren en la cuadrícula de categorías del Administrador. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. El ID del parche es MDVA-34695. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695: Los productos y las categorías no se muestran

El parche MDVA-34695 resuelve el problema de que los productos y las categorías no se muestren en la cuadrícula de categorías del Administrador. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 está instalado. El ID del parche es MDVA-34695. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.4

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.0-2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Valores negativos para `children_count` aparecen en la base de datos después de eliminar las categorías.

<u>Pasos a seguir</u>:

1. Inicie sesión en el servidor de administración.
1. Vaya a **Catálogo > Categorías**.
1. Clic **Agregar subcategoría**.
1. Establecer **nombre de categoría** = *Principal 1* y, a continuación, Guardar.
1. Clic **Agregar subcategoría**.
1. Establecer **nombre de categoría** = *Secundario 1* y, a continuación, Guardar.
1. Clic **Agregar subcategoría**.
1. Establecer **nombre de categoría** = *Secundario 2* y, a continuación, Guardar.
1. Clic **Agregar subcategoría**.
1. Establecer **nombre de categoría** = *Secundario 3* y, a continuación, Guardar. En este punto, esta categoría debería tener un nivel = *5*.
1. Haga clic en **Secundario 1** categoría.
1. Elimine la categoría.

<u>Resultados esperados</u>:

La cuadrícula de categorías muestra productos y categorías, según lo esperado.

<u>Resultados reales</u>:

La cuadrícula de categorías está vacía. Compruebe la `catalog_category_entity` en la base de datos. Tenga en cuenta que `children_count` se volvió negativo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
