---
title: "ACSD-49849: El correo electrónico del cliente se ha sustituido por el correo electrónico de PayPal"
description: Aplique el parche ACSD-49849 para solucionar el problema de Adobe Commerce en el que el correo electrónico del cliente se ha sustituido por correo electrónico de PayPal al realizar un pedido con PayPal Express a través de GraphQL.
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849: el correo electrónico del cliente se sustituye por [!DNL PayPal] email

El parche ACSD-49849 corrige el problema en el que el correo electrónico de un cliente se sustituye por un [!DNL PayPal's] correo electrónico al realizar un pedido con [!DNL PayPal Express] mediante GraphQL. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. El ID del parche es ACSD-49849. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El correo electrónico de un cliente se sustituye por un [!DNL PayPal's] correo electrónico al realizar un pedido con [!DNL PayPal Express] mediante GraphQL.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Habilitar y configurar [!DNL PayPal Express] y establecer **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y cree un producto sencillo.
1. Complete el cierre de compra de invitados con GraphQL. Para obtener más información, consulte [Tutorial de cierre de compra de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) en la documentación para desarrolladores de Adobe Commerce.
1. Uso [!DNL PayPal Express] como forma de pago.
1. Tenga en cuenta el correo electrónico utilizado en el paso donde [configurar el correo electrónico para el carro de compras](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) en la documentación para desarrolladores de Adobe Commerce.
1. Una vez realizado el pedido, vaya al administrador de Adobe Commerce y compruebe el correo electrónico en el pedido creado.

<u>Resultados esperados</u>:

El correo electrónico es el mismo que se establece durante el cierre de compra.

<u>Resultados reales</u>:

El correo electrónico configurado durante la desprotección se anula con el correo electrónico configurado en la [!DNL PayPal] cuenta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
