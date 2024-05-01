---
title: "MDVA-38728: Cambiar la visibilidad del producto crea una reescritura de URL para el sitio web principal"
description: El parche MDVA-38728 resuelve el problema de que, al cambiar la visibilidad del producto del segundo sitio web, se crea una reescritura de URL para el sitio web principal. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-38728. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: ad1d5f82-294d-485d-acd3-28c3cd0fbf56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-38728: Cambiar la visibilidad del producto crea una reescritura de URL para el sitio web principal

El parche MDVA-38728 resuelve el problema de que, al cambiar la visibilidad del producto del segundo sitio web, se crea una reescritura de URL para el sitio web principal. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalado. El ID del parche es MDVA-38728. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al cambiar la visibilidad del producto del segundo sitio web, se crea una reescritura de URL para el sitio web principal.

<u>Pasos a seguir</u>:

1. Cree un sitio web, una tienda y una vista de tienda adicionales.
1. Cree un producto sencillo.
1. Establezca la visibilidad en **No visible individualmente**.
1. Asigne el producto únicamente al segundo sitio web.
1. Rellene todos los demás campos obligatorios.
1. Guarde el producto.
1. Iniciar colas MySQL:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Ir a la lista de productos.
1. Seleccione el producto creado y actualice el atributo de visibilidad mediante la actualización masiva a Catálogo y Buscar.
1. Compruebe la reescritura de la URL.

<u>Resultados esperados</u>:

La reescritura se crea para el segundo sitio web en el que se asigna el producto.

<u>Resultados reales</u>:

La reescritura se crea para el sitio web principal.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
