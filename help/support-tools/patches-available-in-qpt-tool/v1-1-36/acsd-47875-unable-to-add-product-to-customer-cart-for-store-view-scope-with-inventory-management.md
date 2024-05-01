---
title: "ACSD-47875: No se puede agregar un producto al carro para el ámbito de vista de tienda con la administración de inventario"
description: Aplique el parche ACSD-47875 para corregir el problema de Adobe Commerce en el que un producto no se puede agregar a un carro de compras de clientes desde el administrador para un ámbito de vista de tienda determinado con administración de inventario.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875: no se puede agregar un producto al carro para el ámbito de vista de tienda con la administración de inventario

El parche ACSD-47875 corrige el problema en el que un producto no se puede agregar al carro de compras de un cliente desde el administrador para un ámbito de vista de tienda en particular con administración de inventario. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.36 está instalado. El ID del parche es ACSD-47875. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores no pueden añadir un producto al carro de compras de un cliente utilizando **[!UICONTROL Manage Shopping Cart]** función en el Administrador para un ámbito de vista de tienda particular con MSI instalado.

<u>Requisitos previos</u>:

[!DNL Adobe Commerce Inventory Management (MSI)] Los módulos de están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Crear un sitio web, una tienda y una vista de tienda.
1. Crear un origen adicional que no sea *Predeterminado*.
1. Cree un nuevo inventario de stock y asígnelo al nuevo sitio web y al nuevo origen.
1. Cree un nuevo cliente para el nuevo sitio web.
1. Asignar un producto solo al nuevo sitio web; anular la asignación del sitio web predeterminado.

   * Asignar el nuevo origen y establecer cantidad *superior a 0* para el nuevo origen y *0* para el origen predeterminado.

1. Vaya a la **[!UICONTROL Customer Edit]** en la página de administración. Clic **[!UICONTROL Manage Shopping Cart]**.
1. Cambie el ámbito de la vista de tienda a la nueva vista de tienda.
1. Vaya a la **[!UICONTROL Products]** y busque el producto.
1. Seleccione el producto y haga clic en **[!UICONTROL Add selections to my cart]**.

<u>Resultados esperados</u>:

El producto se agrega al carro de compras.

<u>Resultados reales</u>:

* Se genera el siguiente error: *El producto que intenta agregar no está disponible.*
* El producto no se agrega al carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
