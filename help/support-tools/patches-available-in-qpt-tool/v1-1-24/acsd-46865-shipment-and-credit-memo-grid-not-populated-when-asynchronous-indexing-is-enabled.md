---
title: 'ACSD-46865: [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellena cuando [!UICONTROL asynchronous indexing] está habilitado'
description: Aplique el parche ACSD-46865 para solucionar el problema de Adobe Commerce donde [!UICONTROL shipment] y [!UICONTROL credit memo] las cuadrículas no se rellenan cuando [!UICONTROL asynchronous indexing] está activada.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellena cuando [!UICONTROL asynchronous indexing] está habilitado

El parche ACSD-46865 corrige el problema donde [!UICONTROL shipment] y [!UICONTROL credit memo] las cuadrículas no se rellenan cuando [!UICONTROL asynchronous indexing] está activada. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 está instalado. El ID del parche es ACSD-46865. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!UICONTROL Shipment] y [!UICONTROL credit memo] las cuadrículas no se rellenan cuando [!UICONTROL asynchronous indexing] está activada.

<u>Pasos a seguir</u>:

1. En el [!DNL Commerce] Administrador, vaya a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *SÍ*.
2. De nuevo, vaya a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Limpie la caché de configuración.
4. Realice un nuevo pedido de invitado para un producto simple.
5. Corre cron.
6. Abra el pedido en la [!UICONTROL Commerce] Para administrar, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** y generar una factura y un abono.
7. Mover el orden a [!UICONTROL Archive].
8. Cree otro pedido para un producto simple.
9. Corre cron.
10. Vaya al nuevo pedido y genere un nuevo envío, una factura y una nota de abono.
11. Corre cron.
12. Compruebe la [!UICONTROL shipments], [!UICONTROL invoices], y [!UICONTROL credit memo] cuadrículas en el administrador.

<u>Resultados esperados</u>:

Nuevo [!UICONTROL shipment], [!UICONTROL invoice] y [!UICONTROL credit memo] se muestran.

<u>Resultados reales</u>:

Nuevo [!UICONTROL shipment], [!UICONTROL invoice], y [!UICONTROL credit memo] no se muestran.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
