---
title: "ACSD-49497: orden aún procesando después del envío y reembolso parcial"
description: Aplique el parche ACSD-49497 para solucionar el problema de Adobe Commerce en el que el estado del pedido permanece como procesamiento después del envío y se aplica un reembolso parcial.
exl-id: d195bcf4-bb8b-4373-8aad-a5b953b07443
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-49497: orden aún procesando después del envío y reembolso parcial

El parche ACSD-49497 corrige el problema en el que el estado del pedido permanece como procesamiento después del envío y se aplica un reembolso parcial. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 está instalado. El ID del parche es ACSD-49497. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de un nuevo pedido permanece en el *[!UICONTROL Processing]* estado incluso después del envío y se aplica un reembolso parcial.

<u>Pasos a seguir</u>:

1. Cree un pedido con varios elementos.
1. Desde **[!UICONTROL Admin]**, cree una factura para el pedido.
1. Desde **[!UICONTROL Admin]**, crea una nota de abono y reembolsa un artículo sólo parcialmente.
1. Desde **[!UICONTROL Admin]**, solicita el envío de los artículos restantes del pedido.
1. Observe el estado del pedido.

<u>Resultados esperados</u>:

El estado de la solicitud debe ser *[!UICONTROL Complete]*.

<u>Resultados reales</u>:

El estado del pedido permanece *[!UICONTROL Processing]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
