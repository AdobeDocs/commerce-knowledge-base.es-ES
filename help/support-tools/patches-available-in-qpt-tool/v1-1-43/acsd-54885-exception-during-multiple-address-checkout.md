---
title: "ACSD-54885: excepción durante la desprotección de varias direcciones cuando el administrador inicia sesión como cliente"
description: Aplique el parche ACSD-54885 para corregir el problema de Adobe Commerce en el que se produce un error durante la comprobación de varias direcciones cuando el administrador utiliza el *[!UICONTROL Login as Customer]* funcionalidad.
feature: Checkout
role: Admin, Developer
exl-id: 524ec96b-1465-4673-9fbe-1a9c086b7e87
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54885: excepción durante la desprotección de varias direcciones cuando el administrador inicia sesión como cliente

El parche ACSD-54885 corrige el problema en el que se produce un error durante la desprotección de varias direcciones cuando el administrador utiliza el *[!UICONTROL Login as Customer]* funcionalidad. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 está instalado. El ID del parche es ACSD-54885. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error durante la desprotección de varias direcciones cuando el administrador utiliza el *[!UICONTROL Login as Customer]* funcionalidad.

<u>Pasos a seguir</u>:

1. Asegúrese de que *[!UICONTROL Login as Customer]* está activada. Ir a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Cree un producto sencillo.
1. Cree una nueva cuenta de cliente con una dirección.
1. Vaya a la cuenta del cliente en el servidor:

   * Vaya a la **[!UICONTROL Account Information]** pestaña y establezca *[!UICONTROL Allow remote shopping assistance]* = *Sí*.
   * Clic **[!UICONTROL Login as Customer]**.

1. Añada el producto al carro de compras y continúe en *[!UICONTROL Checkout with multiple addresses]*.
1. Actualice la cantidad del producto.
1. Intente volver al carro de compras.

<u>Resultados esperados</u>:

Puede actualizar el carro de compras y usar el cierre de compra de varias direcciones.

<u>Resultados reales</u>:

Recibe el siguiente error al volver al carro de compras.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
