---
title: "ACSD-47910: pedidos, facturas, envíos y notas de abono que faltan en las cuadrículas de entidades respectivas"
description: Aplique el parche ACSD-47910 para solucionar el problema de Adobe Commerce en el que faltan pedidos, facturas, envíos y notas de abono en las cuadrículas de entidades correspondientes.
exl-id: 4eb897ec-16e4-420e-89a6-c8f7c8740303
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-47910: faltan pedidos, facturas, envíos y notas de abono en las cuadrículas de entidades correspondientes

El parche ACSD-47910 corrige el problema en el que faltan pedidos, facturas, envíos y notas de abono en las cuadrículas de entidades correspondientes. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 está instalado. El ID del parche es ACSD-47910. La versión en la que se solucionará este problema aún no está disponible.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con las versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Faltan pedidos, facturas, envíos y notas de abono en las respectivas cuadrículas de entidades.

<u>Pasos a seguir</u>:

1. Activar **[!UICONTROL Asynchronous indexing]** en **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Haz dos pedidos.
1. Ejecute el cron para sincronizar esos pedidos con la cuadrícula.
1. Abra uno de los pedidos y prepárelo para facturarlo. NO ENVIAR LA FACTURA AÚN.
1. Haga un nuevo pedido listo para colocarlo en el front-end. NO HAGA CLIC AÚN EN EL BOTÓN REALIZAR PEDIDO.
1. Añadir un `sleep(30)` en el `foreach` en `NotSyncedDataProvider::L43`.
1. Ejecutar `bin/magento cron:run`.
1. Ahora coloque el nuevo pedido.
1. Facturar el pedido anterior.
1. Vuelva a ejecutar el cron esperando que se sincronice el nuevo orden.
1. Vaya a la cuadrícula de pedidos en Admin.

<u>Resultados esperados</u>:

El nuevo orden debe aparecer en la cuadrícula del orden.

<u>Resultados reales</u>:

La actualización de pedido anterior se ha sincronizado con la cuadrícula (**[!UICONTROL status: Processing]**). El nuevo orden nunca aparece en la cuadrícula.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
