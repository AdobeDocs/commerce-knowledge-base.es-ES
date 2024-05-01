---
title: "ACSD-52287: El estado de los pedidos archivados no cambia"
description: Aplique el parche ACSD-52287 para solucionar el problema de Adobe Commerce en el que el estado de los pedidos archivados no cambia de *completado* a *cerrado* en la cuadrícula después de enviar la nota de crédito.
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-52287: El estado de los pedidos archivados no cambia

El parche ACSD-52287 corrige el problema en el que el estado de los pedidos archivados no cambia de *completado* hasta *cerrado* en la cuadrícula después de enviar la nota de abono. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 está instalado. El ID del parche es ACSD-52287. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de los pedidos archivados no cambia de *completado* hasta *cerrado* en la cuadrícula después de enviar la nota de abono.

<u>Pasos a seguir</u>:

1. Configurar *[!UICONTROL Asynchronous Indexing]*.
   * En la barra lateral de Administración, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * En el panel izquierdo, expanda **[!UICONTROL Advanced]** y elija **[!UICONTROL Developer]** debajo.
   * Expanda el **[!UICONTROL Grid Settings]** sección.
   * Establecer *[!UICONTROL Asynchronous indexing]* hasta *Sí*.
   * Clic **[!UICONTROL Save Config]**.
1. Configure las variables *[!UICONTROL Order Archive]*.
   * En la barra lateral de Administración, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * En el panel izquierdo, expanda **[!UICONTROL Sales]** y elija **[!UICONTROL Sales]** debajo.
   * Expanda el **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** sección.
   * Establecer *[!UICONTROL Enable Archiving]* hasta *Sí* (Deje el resto de las configuraciones como predeterminadas).
   * Clic **[!UICONTROL Save Config]**.
1. Realice un pedido en el front-end.
1. Ejecute el [!DNL cron]  para que el orden aparezca en *[!UICONTROL Admin Order Grid]*.
1. Facturar y enviar el pedido para actualizar el estado del pedido a *Completar*.
1. Ejecute el [!DNL cron]  para actualizar el *[!UICONTROL Sales Order Grid]* con el último estado de pedido.
1. Archivar el pedido.
1. Vaya a la *[!UICONTROL Archived order grid]*.
1. Abra el pedido archivado y devuélvalo sin conexión creando un [!UICONTROL Credit Memo] para realizar la [!UICONTROL Order status]: *Cerrado*.
1. Ejecute el [!DNL cron] por un par de veces.
1. Compruebe la *[!UICONTROL Archived order grid]* para el nuevo estado de pedido.

<u>Resultados esperados</u>:

El orden se muestra como *Cerrado*.

<u>Resultados reales</u>:

El orden se muestra como *Completar*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
