---
title: "ACSD-51230: se ha eliminado la cuenta de la tarjeta regalo"
description: Aplique el parche ACSD-51230 para corregir el problema de Adobe Commerce en el que la cuenta de tarjeta de regalo se elimina cuando se procesa el reembolso parcial de un producto simple de un pedido.
exl-id: 4322a175-3641-468a-8a0f-fcbad90c758f
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-51230: se elimina la cuenta de la tarjeta regalo

El parche ACSD-51230 corrige el problema en el que la cuenta de la tarjeta regalo se elimina cuando el reembolso parcial de un producto simple se procesa a partir de un pedido. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. El ID del parche es ACSD-51230. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cuenta de tarjeta regalo se elimina cuando el reembolso parcial de un producto simple se procesa desde un pedido.

<u>Pasos a seguir</u>:

1. Cree un pedido con una *Tarjeta regalo* y una *producto simple* (por ejemplo, *añadir: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (cualquier forma de pago y envío funciona).
1. Facturar el pedido.
1. Ir a **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Se crea una cuenta para la tarjeta regalo.
1. Ahora, vaya a **[!UICONTROL Order]** y cree un **[!UICONTROL Credit Memo]**.
1. Cambie la cantidad de la *Tarjeta regalo* a 0 y actualícelo. Esto creará un reembolso parcial para el *producto simple*.
1. Haga clic en **[!UICONTROL Refund]**.
1. Ahora actualice el **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Se elimina la cuenta recién creada.

<u>Resultados esperados</u>

La cuenta de la tarjeta regalo está disponible para su uso, ya que el reembolso no se creó para la tarjeta regalo.

<u>Resultados reales</u>

La cuenta de la tarjeta regalo se elimina y la tarjeta regalo no se devuelve.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
