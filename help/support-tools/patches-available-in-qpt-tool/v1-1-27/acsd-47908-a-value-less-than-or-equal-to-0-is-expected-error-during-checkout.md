---
title: "ACSD-47908: *Se espera un valor menor o igual a 0* error durante la desprotección"
description: Aplique el parche ACSD-47908 para corregir el error de Adobe Commerce *Se espera un valor menor o igual a 0* al seleccionar el origen y la cantidad en el paso de envío durante el cierre de compra.
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908: *Se espera un valor menor o igual a 0* error durante el cierre de compra

El parche ACSD-47908 corrige el error *Se espera un valor menor o igual a 0* al seleccionar el origen y la cantidad en el paso de envío durante el cierre de compra. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. El ID del parche es ACSD-47908. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se genera el siguiente error al seleccionar el origen y la cantidad en el paso de envío durante la desprotección: *Se espera un valor menor o igual a 0*.

<u>Requisitos previos</u>:

Instale los módulos de Adobe Commerce Inventory management (MSI).

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** y configurar varias fuentes.
1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** y cree un nuevo inventario de stock.
   * Ahora asigne las fuentes al nuevo stock.
1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y editar al menos un producto.
   * Asegúrese de que los productos estén asignados a los nuevos orígenes y especifique la cantidad disponible.
1. Ir a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** y cree un nuevo pedido.
1. Agregue esos productos al pedido y colóquelo.
1. Clic **[!UICONTROL Ship]**.
1. Seleccione el origen desde el que desea realizar el envío.
1. Especifique la cantidad de cada artículo que desea enviar.
1. Vuelva a cargar la página.
1. Haga clic en **[!UICONTROL Proceed to Shipment]**.

<u>Resultados esperados</u>:

La nueva página de envío se abre sin ningún error.

<u>Resultados reales</u>:

* No se puede validar la cantidad introducida.
* Se genera el siguiente error: *Introduzca un valor menor o igual que 0*.

  Sin embargo, el error es incoherente y puede no aparecer siempre.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
