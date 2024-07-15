---
title: "MDVA-37984: Visual Merchandiser no funciona correctamente cuando se aplican actualizaciones de ensayo"
description: El parche MDVA-37984 resuelve el problema en el que la funcionalidad "Coincidir producto por regla" de Visual Merchandiser no filtra los productos correctamente cuando se aplican actualizaciones de ensayo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-37984. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984: Visual Merchandiser no funciona correctamente cuando se aplican actualizaciones de ensayo

El parche MDVA-37984 resuelve el problema en el que la funcionalidad &quot;Coincidir producto por regla&quot; de Visual Merchandiser no filtra los productos correctamente cuando se aplican actualizaciones de ensayo. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. El ID del parche es MDVA-37984. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La funcionalidad &quot;Hacer coincidir producto por regla&quot; de Visual Merchandiser no filtra los productos correctamente cuando se aplican las actualizaciones de ensayo.

<u>Pasos a seguir</u>:

1. Cree una actualización de programación para cualquier producto existente.
   * Establecer valores diferentes para `entity_id` y `row_id`.
1. Cree un nuevo producto configurable y, a continuación, un producto simple (por lo que el nuevo producto `entity_id` y `row_ids` también son diferentes).
   * Para facilitar la réplica del problema, establezca un valor de cantidad distinguible para el producto simple; por ejemplo, 5000.
1. Vaya a una categoría > **Productos de la categoría** y habilite **Hacer coincidir productos por regla**.
1. Ahora seleccione &quot;Cantidad&quot; como atributo, &quot;Mayor&quot; como operador y &quot;4500&quot; como valor.
1. Haga clic en **guardar**.

<u>Resultados esperados</u>:

Se muestra el producto configurable recién creado.

<u>Resultados reales</u>:

No aparece el producto configurable recién creado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
