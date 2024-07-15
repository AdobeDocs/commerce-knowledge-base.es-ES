---
title: "Parche MDVA-32634: la categoría de movimiento en la jerarquía url_path es incorrecta"
description: El parche MDVA-32634 resuelve el problema en el que la url\_path de la categoría de catálogo no cambia después de mover la categoría en la jerarquía. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Parche MDVA-32634: la categoría de movimiento en la jerarquía url_path es incorrecta

El parche MDVA-32634 resuelve el problema en el que la url\_path de la categoría de catálogo no cambia después de mover la categoría en la jerarquía. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.4-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.1 - 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al mover una categoría de catálogo en la jerarquía, se produce una url\_path incorrecta. La url\_path de la categoría asignada al ámbito de almacén predeterminado \[ **id:0** \] permanece sin cambios después de mover la categoría en la jerarquía.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de Commerce. Cree la siguiente estructura de categorías en la categoría raíz: move-cat-sub-move-cat-sub-move-cat2 new-cat-move
1. Compruebe la categoría \[ url\_path \] atributo \[ id: 120 \] para la asignación de valores en la tabla \[ catalog\_category\_entity\_varchar \] mediante la siguiente consulta:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Debe proporcionarle el siguiente resultado:

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Los valores \[ url\_path \] se generaron y se asignaron al ámbito de All Store \[ 0 \]. Esto es correcto en comparación con una instancia sin B2B.
1. Vaya a la lista de categorías back-end, arrastre \[ move-cat \] y suéltelo en \[ new-cat-move \]. Ahora la categoría debería tener el siguiente aspecto: new-cat-move-cat-sub-move-cat2
1. Compruebe la tabla \[ catalog\_category\_entity\_varchar \] mediante la siguiente consulta:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>Resultados esperados</u>:

La url\_path asignada a todo el ámbito de almacenamiento \[ 0 \] también debe actualizarse con la nueva ruta.

<u>Resultados reales</u>:

La url\_path asignada a todo el ámbito de almacenamiento \[ 0 \] permanece sin cambios, aunque no haya ninguna ruta de este tipo disponible después del movimiento. Además, tiene nuevos valores url\_path creados para cada tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
