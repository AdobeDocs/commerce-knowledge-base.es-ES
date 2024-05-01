---
title: "ACSD-48694: Error solicitado de cambio de estado no válido que impide al cliente realizar el pedido"
description: Aplique el parche ACSD-48694 para solucionar el problema de Adobe Commerce donde el error *Se ha solicitado un cambio de estado no válido* impide que un cliente realice un pedido.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694: *Cambio de estado no válido solicitado* error impide que el cliente realice el pedido

El parche ACSD-48694 corrige el problema donde el error *Cambio de estado no válido solicitado* evita que un cliente realice un pedido. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. El ID del parche es ACSD-48694. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El error *Cambio de estado no válido solicitado* evita que un cliente realice un pedido.

<u>Pasos a seguir</u>:

1. Añada un ligero retraso durante la `/estimate-shipping-methods` solicitud incluyendo un `sleep()` en `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` función, de modo que la `/estimate-shipping-methods` La solicitud se completa después de que `/shipping-information` al pasar del paso de envío al paso de pago durante el cierre de compra.
1. Configure la sesión para utilizar [!DNL Redis] con el *disable_locked: 1* configuración.
1. Abrir **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** y habilitar *[!UICONTROL Persistent Shopping Cart]*.
1. Inicie sesión como cliente y añada un producto al carro de compras.
1. Deje que caduque la sesión del cliente. La cookie persistente y el carro de compras aún persisten.
1. Ahora ve a Pago y envío, agrega la dirección de envío y navega a la sección de pago.
1. Vuelva a la página principal o a cualquier otra página e inicie sesión con la cuenta del cliente.
1. Deje que la sesión caduque de nuevo.
1. Ahora ve directamente a la página de pago y navega al paso de pago.
1. Intente realizar el pedido.

<u>Resultados esperados</u>:

* No hay ningún error.
* El pedido se ha realizado correctamente y *Gracias.* se muestra la página.

<u>Resultados reales</u>:

El error *Cambio de estado no válido solicitado* se muestra, pero se realiza el pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
