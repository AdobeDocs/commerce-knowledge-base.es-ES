---
title: "ACSD-51238: El origen de inventario se elimina al actualizar un producto configurable y editar el precio"
description: Aplique el parche ACSD-51238 para solucionar el problema de Adobe Commerce en el que se elimina el origen de inventario al actualizar un producto configurable y editar el precio.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238: el origen de inventario se elimina al actualizar un producto configurable y editar el precio

El parche ACSD-51238 corrige el problema en el que se elimina el origen de inventario al actualizar un producto configurable y editar el precio. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. El ID del parche es ACSD-51238. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El origen de inventario se elimina al actualizar un producto configurable y editar el precio.

<u>Pasos a seguir</u>:

1. Instalar **[!DNL Adobe Commerce]** con **[!DNL Inventory module]**
1. Vaya a la **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** y crear *dos fuentes* y *dos acciones*.
1. Crear un **[!UICONTROL configurable product]** y asignarlo a **[!UICONTROL default sources]** o **[!UICONTROL newly created sources]**.
1. Haga clic en **[!UICONTROL next button]** y *guardar* el producto.
1. Ahora edite lo mismo **[!UICONTROL Configurable Product]** y haga clic en **[!UICONTROL Edit Configuration]** dentro de **[!UICONTROL Configuration tab]**.
1. Entrada `Step 3: Bulk Images,Price and Quantity`, cambie la `price` y salir `Quantity` y `Images` hasta `Skip quantity at this time` y `Skip image uploading at this time` respectivamente.
1. Haga clic en **[!UICONTROL next button]** y generar el producto.

<u>Resultados esperados</u>

La cantidad por origen dentro de **[!UICONTROL Configuration tab]** no debería estar vacío.

<u>Resultados reales</u>

La cantidad por origen dentro de **[!UICONTROL Configuration tab]** está vacío.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en el [!DNL Quality Patches Tool] guía.
