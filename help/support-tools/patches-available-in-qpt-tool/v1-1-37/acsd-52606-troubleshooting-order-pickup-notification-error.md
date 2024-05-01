---
title: 'ACSD-52606: mensaje de error mostrado cuando el usuario hace clic en "Notificar pedido está listo para su recogida"'
description: Aplique el parche ACSD-52606 para solucionar el problema de Adobe Commerce, donde se muestra un mensaje de error cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606: mensaje de error que se muestra cuando el usuario hace clic en &quot;Notificar pedido está listo para su recogida&quot;

El parche ACSD-52606 corrige el problema en el que se mostraba un mensaje de error *Su pedido no está listo para recoger* cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.37 está instalado. El ID del parche es ACSD-52606. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un mensaje de error *Su pedido no está listo para recoger* se muestra en la pantalla cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Requisitos previos</u>:

Los módulos de inventario están instalados.

<u>Pasos a seguir</u>:

1. Instale una instancia nueva.
1. Crear un nuevo origen y stock.
1. Asigne el nuevo origen al sitio web predeterminado.
1. Habilite la ubicación de recogida para el origen recién creado.
1. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** y habilitar **[!UICONTROL In-Store Delivery]**.
1. Crear un *En stock* producto simple con *CANTIDAD=0* para todas las existencias y *[!UICONTROL Manage Stock = No]* y asígnelo a ambos orígenes.
1. Cree un pedido desde el front-end con el producto creado en el paso anterior, eligiendo *[!UICONTROL In-Store Pickup]* como método de envío.
1. En Administración, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Clic **[!UICONTROL Notify order is ready for pickup]**.

<u>Resultados esperados</u>:

Se le notificará sin errores.

<u>Resultados reales</u>:

Recibe el siguiente mensaje de error: *Su pedido no está listo para recoger*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
