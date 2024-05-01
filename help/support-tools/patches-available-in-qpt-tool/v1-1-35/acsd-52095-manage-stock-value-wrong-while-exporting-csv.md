---
title: "ACSD-52095: La administración del valor de stock es incorrecta al exportar el CSV"
description: Aplique el parche ACSD-52095 para corregir el problema de Adobe Commerce en el que el valor de stock de administración de productos es incorrecto al exportar CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095: [!UICONTROL Manage Stock] el valor es incorrecto al exportar el CSV

El parche ACSD-52095 corrige el problema en el que el producto `manage_stock` el valor es incorrecto al exportar el CSV. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. El ID del parche es ACSD-52095. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El `manage_stock` el valor se establece incorrectamente en 0 en el archivo CSV después de la exportación del producto.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** y establecer **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Cree un nuevo producto y guárdelo.
1. Ir a **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Seleccionar *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* y exportar los productos.
1. Compruebe el archivo CSV generado: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. De nuevo, vaya a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** y establezca  **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Ir a **Sistema** > **Exportar**.
Seleccionar *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Compruebe el archivo CSV generado: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Abra el producto en Admin y vaya a **[!UICONTROL Advanced Inventory]** y compruebe la **[!UICONTROL Manage Stock]** valor.

<u>Resultados esperados</u>

El **[!UICONTROL Manage Stock]** el valor es *1* cuando esté habilitado para los productos.

<u>Resultados reales</u>

El **[!UICONTROL Manage Stock]** el valor es *0* cuando esté habilitado para los productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
