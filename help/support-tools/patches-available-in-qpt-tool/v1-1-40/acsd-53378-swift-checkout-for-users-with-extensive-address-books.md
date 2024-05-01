---
title: "ACSD-53378: experiencia de cierre de compra mejorada para clientes con libretas de direcciones extensas"
description: Aplique el parche ACSD-53378 para solucionar el problema de Adobe Commerce donde haya problemas de rendimiento causados por grandes volúmenes de direcciones de clientes.
feature: Customers, Checkout
role: Admin
exl-id: 561462fd-844b-40e0-9ccd-25f7aa9be161
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-53378: experiencia de pago mejorada para clientes con libretas de direcciones extensas

El parche ACSD-53378 corrige el problema en el que hay problemas de rendimiento causados por grandes volúmenes de direcciones de clientes. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 está instalado. El ID del parche es ACSD-53378. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El rendimiento de Adobe Commerce se vuelve muy lento si un cliente tiene un gran número de direcciones.

Si la opción de configuración *[!UICONTROL Enable search address]* bajo **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** se activa, la libreta de direcciones del cliente completa ya no se procesará por completo. El número de direcciones de clientes procesadas viene determinado por la configuración *[!UICONTROL Customer Addresses Limit]* bajo  **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo desde el administrador.
1. Cree un cliente con una libreta de direcciones extensa que contenga 1000 direcciones.
1. Vaya al front-end y añada el producto al carro de compras.
1. Abra la página del carro de compras.

<u>Resultados esperados</u>:

El recuento de direcciones de clientes no afecta al tiempo de respuesta.

<u>Resultados reales</u>:

La página del carro de compras tarda mucho tiempo en cargarse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
