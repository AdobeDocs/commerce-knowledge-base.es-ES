---
title: "ACSD-47520: los clientes pierden puntos de recompensa cuando se crea una nota de crédito"
description: Aplique el parche ACSD-47520 para solucionar el problema de Adobe Commerce en el que los clientes pierden puntos de recompensa cuando se crea un abono.
exl-id: 748b4e05-981d-49f6-a4f5-b121d57085f4
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47520: los clientes pierden puntos de recompensa cuando se crea una nota de crédito

El parche ACSD-47520 corrige el problema en el que los clientes pierden puntos de recompensa cuando se crea una nota de crédito. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 está instalado. El ID del parche es ACSD-47520. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con las versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los clientes pierden puntos de recompensa al crear una nota de crédito.

<u>Pasos a seguir</u>:

1. Vaya a Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Cambie la configuración:
   * **[!UICONTROL Enable Reward Points Functionality]** = _Sí_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Sí_
   * **[!UICONTROL Customers May See Reward Points History]** = _Sí_
   * **[!UICONTROL Refund Reward Points Automatically]** = _No_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Sí_
1. Vaya a la pestaña Administración > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** y haga clic en **[!UICONTROL Add New Rate]**.
1. Añada una nueva tasa (1:1) y vacíe la caché.
1. Cree un cliente y añada 10 puntos de recompensa a esta cuenta.
1. Vaya a la pestaña Administración > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Seleccione el cliente creado en el paso anterior.
1. Seleccione cualquier producto cuyo precio sea mayor que los puntos de recompensa.
1. Realice un pedido a través de cualquier método de pago y los puntos de recompensa.
1. Cree una factura para el pedido.
1. Crear una nota de crédito, pero no reembolsar los puntos de recompensa.

<u>Resultados esperados</u>:

* El administrador puede reembolsar los puntos de recompensa.

* El estado del pedido se cerrará.

<u>Resultados reales</u>:

* No hay forma de reembolsar los puntos de recompensa.

* El estado del pedido es **[!UICONTROL Completed]**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
