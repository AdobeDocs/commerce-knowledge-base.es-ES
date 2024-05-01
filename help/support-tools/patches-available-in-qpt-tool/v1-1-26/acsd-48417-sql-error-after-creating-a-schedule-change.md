---
title: "ACSD-48417: Error SQL después de crear un cambio de programación"
description: Aplique el parche ACSD-48417 para corregir el problema de Adobe Commerce en el que aparece un error SQL después de crear un cambio de programación para un producto y guardar otro.
exl-id: 2bbf3bb5-dec8-43b3-81f1-be0dc53d1f46
feature: Storage
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417: Error SQL después de crear un cambio de programación

El parche ACSD-48417 corrige el problema en el que aparece un error SQL después de crear un cambio de programación para un producto y guardar otro. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 está instalado. El ID del parche es ACSD-48417. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Aparece un error de SQL después de crear un cambio de programación para un producto y guardar otro producto.

<u>Pasos a seguir</u>:

1. Instalar Magento 2.4, desarrollar EE + Datos de muestra.
1. Vaya al panel de administración > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Edite cualquier producto (por ejemplo, Joust Duffle Bag [SKU: 24 MB01]).
1. Programar una nueva actualización:
   * Seleccionar **[!UICONTROL Save as a New Update]**
   * Nombre de la actualización: &quot;Update 1&quot;
   * Fecha de inicio: hora actual +1 min
   * Fecha de finalización: hora actual +1 hora
   * Modificar el nombre del producto a: &quot;Joust Duffle Bag 2&quot;
   * Guarde el producto.
1. Vaya a CLI y ejecute cron y espere hasta que se aplique la programación.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. De nuevo, vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y editar cualquier producto configurable (por ejemplo, Chaz Kangeroo Hoodie) [SKU: MH01]).

   * Deshabilite todas las variantes. Vaya a la columna Actions > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Guarde el configurable.

<u>Resultados esperados</u>:

No se produce ningún error al guardar el producto.

<u>Resultados reales</u>:

Se produce el siguiente error:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
