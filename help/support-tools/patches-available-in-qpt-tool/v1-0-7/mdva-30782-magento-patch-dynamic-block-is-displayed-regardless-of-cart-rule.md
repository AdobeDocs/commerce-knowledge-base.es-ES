---
title: "MDVA-30782: el bloque dinámico se muestra independientemente de la regla del carro de compras"
description: El parche MDVA-30782 corrige el problema de que se muestra un bloque dinámico independientemente de la regla del carro de compras. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 88da8853-aae7-4fd9-82ba-a4e9fc99cf53
feature: Cache, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30782: el bloque dinámico se muestra independientemente de la regla del carro de compras

El parche MDVA-30782 corrige el problema de que se muestra un bloque dinámico independientemente de la regla del carro de compras. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 está instalado. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.5-p1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El bloque dinámico se muestra en la página incluso cuando no se cumple la condición de regla de precio del catálogo relacionada.

<u>Pasos a seguir</u>:

1. Cree dos productos.
1. Cree una regla de precios de catálogo aplicable solo a uno de estos productos.
1. Cree un bloque dinámico y asígnele la regla de precio de catálogo recién creada.
1. Cree un widget con los siguientes parámetros:
   * Tipo = Rotador de bloque dinámico
   * Bloques dinámicos para mostrar = Bloques dinámicos especificados
   * Especificar bloques dinámicos = bloquear formulario paso \#3Layout Actualizaciones (puede ser cualquier)
   * Mostrar en = Todos los tipos de productos
   * Contenedor = Información auxiliar del producto
1. Realice la reindexación y el vaciado de la caché.
1. Compruebe ambas páginas de productos para ver el formulario de bloque dinámico, paso \#3

<u>Resultados esperados</u>:

El bloque dinámico solo aparece en la primera página de producto.

<u>Resultados reales</u>:

El bloque dinámico aparece en ambas páginas de producto. Con Bloques dinámicos para mostrar = Regla de precio de catálogo relacionada en el paso \#3, el resultado es el mismo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
