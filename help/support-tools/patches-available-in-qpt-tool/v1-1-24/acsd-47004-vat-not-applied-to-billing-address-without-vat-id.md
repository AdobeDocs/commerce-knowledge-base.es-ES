---
title: "ACSD-47004: IVA no aplicado a la dirección de facturación sin ID de IVA"
description: Aplique el parche ACSD-47004 para solucionar el problema de Adobe Commerce en el que el IVA no se aplica a una dirección de facturación sin ID de IVA.
exl-id: 04706219-be1d-4d9a-a8bf-f5c24b45076d
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# ACSD-47004: IVA no aplicado a la dirección de facturación sin ID de IVA

El parche ACSD-47004 soluciona el problema de que el IVA no se aplica a una dirección de facturación sin un ID de IVA. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)  1.1.24 está instalado. El ID del parche es ACSD-47004. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El IVA no se aplica a una dirección de facturación sin un ID de IVA.

<u>Pasos a seguir</u>:

1. Abra el [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** y configure el **[!UICONTROL Enable Automatic Assignment to Customer Group]** hasta *[!UICONTROL Yes]*.
1. Defina grupos diferentes para las validaciones de ID de IVA. Por ejemplo:
   ![Validaciones de ID de IVA](/help/support-tools/patches-available-in-qpt-tool/assets/vat-id-validations.png)
1. Registre un cliente nuevo.
1. Añadir una nueva dirección predeterminada sin IVA. Por ejemplo:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Compruebe que el grupo del cliente permanece [!UICONTROL General].
1. Edita esta dirección y añade un número de IVA válido:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Asegúrese de que el grupo del cliente ha cambiado a [!UICONTROL Retailer].
1. Edita la dirección y elimina el número de IVA:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Resultados esperados</u>:

El grupo de clientes se cambia al predeterminado [!UICONTROL General] agrupar automáticamente.

<u>Resultados reales</u>:

El grupo de clientes no cambia al predeterminado [!UICONTROL General] agrupar automáticamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
