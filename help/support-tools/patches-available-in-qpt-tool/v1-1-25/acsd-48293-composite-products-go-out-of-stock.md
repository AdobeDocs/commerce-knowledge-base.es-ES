---
title: "ACSD-48293: productos compuestos agotados al agotarse los productos infantiles repuestos"
description: Aplique el parche ACSD-48293 para corregir el problema de Adobe Commerce en el que los productos compuestos no están en existencias cuando los productos secundarios agotados vuelven a estar en existencias.
exl-id: 74ca34fe-e015-4daf-a608-4756c8ab3558
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48293: productos compuestos agotados al agotarse los productos infantiles repuestos

El parche ACSD-48293 soluciona el problema de que los productos compuestos se agotan cuando los productos secundarios agotados vuelven a estar en existencias. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 está instalado. El ID del parche es ACSD-48293. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos compuestos se agotan cuando los productos secundarios que se agotaron vuelven a estar en existencias.

<u>Pasos a seguir</u>:

1. Crear un sitio web, una tienda y una vista de tienda secundarios.
1. Cree dos orígenes y existencias y asígnelos a cada sitio web.
1. Active la opción mostrar productos sin existencias en **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Cree un producto configurable con un producto asociado utilizando la fuente de stock del sitio web principal (cantidad establecida = 1).
1. Realice un pedido del producto configurable.
1. Corre el cron.
1. Abra el producto configurable de la tienda y confirme que está agotado.
1. Abra el producto configurable desde el [!UICONTROL Admin] y configure el **[!UICONTROL Manage Stock Option]** hasta *[!UICONTROL No]*.
1. Corre el cron.
1. Envíe el pedido y añada la cantidad al producto simple para que esté disponible.
1. Corre el cron.
1. Compruebe la disponibilidad del producto en la tienda.

<u>Resultados esperados</u>:

El producto configurable está en stock.

<u>Resultados reales</u>:

El producto configurable está agotado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
