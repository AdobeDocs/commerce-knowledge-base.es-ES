---
title: "ACSD-46865: [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellenaron cuando [!UICONTROL asynchronous indexing] está habilitado"
description: Aplique el parche ACSD-46865 para solucionar el problema de Adobe Commerce en el que las cuadrículas [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellenan cuando [!UICONTROL asynchronous indexing] está habilitado.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellenaron cuando [!UICONTROL asynchronous indexing] está habilitado

La revisión ACSD-46865 corrige el problema en el que las cuadrículas [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellenan cuando [!UICONTROL asynchronous indexing] está habilitado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. El ID del parche es ACSD-46865. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las cuadrículas [!UICONTROL Shipment] y [!UICONTROL credit memo] no se rellenan cuando [!UICONTROL asynchronous indexing] está habilitado.

<u>Pasos a seguir</u>:

1. En el administrador de [!DNL Commerce], vaya a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *SÍ*.
2. De nuevo, vaya a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Limpie la caché de configuración.
4. Realice un nuevo pedido de invitado para un producto simple.
5. Corre cron.
6. Abra el pedido en el administrador de [!UICONTROL Commerce] yendo a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** y genere una factura y un abono.
7. Mover la orden a [!UICONTROL Archive].
8. Cree otro pedido para un producto simple.
9. Corre cron.
10. Vaya al nuevo pedido y genere un nuevo envío, una factura y una nota de abono.
11. Corre cron.
12. Compruebe las cuadrículas [!UICONTROL shipments], [!UICONTROL invoices] y [!UICONTROL credit memo] en el administrador.

<u>Resultados esperados</u>:

Se muestran los nuevos [!UICONTROL shipment], [!UICONTROL invoice] y [!UICONTROL credit memo].

<u>Resultados reales</u>:

No se muestran los nuevos [!UICONTROL shipment], [!UICONTROL invoice] y [!UICONTROL credit memo].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
