---
title: 'MDVA-34850: las muestras que no se tachan en el inventario llegan a "0"'
description: El parche MDVA-34850 corrige el problema de que las muestras no se eliminan cuando el inventario alcanza "0" y no están visibles en el vínculo de la página de detalles del producto (PDP) a ninguna otra muestra en existencia. La **Mostrar productos sin existencias** también se establece en *Sí* en la configuración de administración. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850: las muestras no tachadas del inventario llegan a &quot;0&quot;

El parche MDVA-34850 corrige el problema de que las muestras no se eliminan cuando el inventario alcanza &quot;0&quot; y no están visibles en el vínculo de la página de detalles del producto (PDP) a ninguna otra muestra en existencia. El **Mostrar productos sin existencias** también se establece en *Sí* en la configuración de administración. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p2

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce local y Adobe Commerce en la infraestructura en la nube 2.3.1 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las opciones de Producto sin existencias no se muestran en la página PDP cuando el inventario predeterminado no está en uso y **Mostrar productos sin existencias** La configuración de está activada.

<u>Requisitos previos</u>:

* Instale el inventario de varios orígenes (MSI).
* Habilitar la visualización de productos sin existencias en [Opciones de stock de inventario](https://docs.magento.com/user-guide/configuration/catalog/inventory.html).

<u>Pasos a seguir</u>:

1. Crear nuevo inventario de stock \[Nuevo inventario\], asignándole todos los sitios web y el origen anterior. Ahora, las existencias predeterminadas no deben estar en uso.
1. Crear un [producto configurable](https://docs.magento.com/user-guide/catalog/product-create-configurable.html) añadiendo tres opciones de tamaño \[S,M,L\].
1. Abra cada opción y añada cantidades asignando únicamente el origen personalizado \[new\_source\] creado. Establezca \[Estado de origen\] en \[En stock\].
1. Reindexe y compruebe el producto configurable desde el front-end. Las tres opciones deben ser visibles.
1. Abra un producto simple asignado a \[size:S\] desde el backend y establezca el \[Estado de origen\] en \[Agotado\], actualice también la cantidad a 0. Reindexe y compruebe el producto configurable desde el front-end.

<u>Resultados esperados</u>:

Dado que la opción Mostrar productos sin existencias está activada, deberían aparecer las tres opciones. La opción Agotada \[S\] debe estar desactivada y tachada. Debe mostrar 2 x de 1 producto de opción con precio = 12 x 2 en los detalles de pedido del front-end y el back-end.

<u>Resultados reales</u>:

La opción Agotado está oculta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para más información sobre otros parches disponibles en QPT, consulte la [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
