---
title: "MDVA-39181: Las reglas de producto relacionadas muestran productos de la categoría sin definir en la regla"
description: El parche MDVA-39181 resuelve el problema en el que las reglas de producto relacionadas muestran productos de una categoría no definida en la regla. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-39181. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181: Las reglas de producto relacionadas muestran productos de la categoría sin definir en la regla

El parche MDVA-39181 resuelve el problema en el que las reglas de producto relacionadas muestran productos de una categoría no definida en la regla. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-39181. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las reglas de productos relacionadas muestran productos de categorías no definidas en la regla.

<u>Requisitos previos</u>:

Instalar datos de ejemplo.

<u>Pasos a seguir</u>:

1. Cree una marca de atributo y agréguela al conjunto de atributos **Tops**.
1. Elige las chaquetas **Josie**, **Augusta** e **Ingrid** para agregarlas al Brand Kitty desde **Mujer** > **Tops** > **Chaquetas de la categoría**.
1. Elige las chaquetas **Beaumont**, **Hyperion** y **Kenobi** para añadirlas a Brand Kitty desde **Hombres** > **Tops** > **Categoría de chaqueta**.
1. Crear un producto relacionado con:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Productos para hacer coincidir:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Productos para mostrar:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Abra el SKU WJ04 en la parte frontal y compruebe los productos relacionados.
1. Actualice el identificador de categoría de **Mujeres** > **Tops** > **Chaquetas** en caso de que sea diferente a esto.

<u>Resultados esperados</u>:

En los productos relacionados solo se muestran los productos de la misma marca y la misma categoría secundaria.

<u>Resultados reales</u>:

Los productos relacionados se muestran de la misma marca pero de una categoría principal aleatoria.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
